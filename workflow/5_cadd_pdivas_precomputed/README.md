# [CADD](https://github.com/kircherlab/CADD-scripts) and [PDIVAS](https://github.com/shiro-kur/PDIVAS?tab=readme-ov-file) annotations

For this step you will need [vcfanno](https://github.com/brentp/vcfanno). You can install it with [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)/[mamba](https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html):

```bash
mamba create -n vcfanno bioconda::vcfanno
```

To start annotation you need:

1. Download PDIVAS precomputed variants
```bash
gsutil -m cp -r \
  "gs://pdivas/PDIVAS_precomputed" \
  .
```
2. Download CADD precomputed variants
```bash
wget -c https://krishna.gs.washington.edu/download/CADD/v1.7/GRCh38/whole_genome_SNVs.tsv.gz -O cadd_precomputed_snv.tsv.gz
```
3. Create vcfanno `ann.conf` config file with the following text
```plaintext
[[annotation]]
file="PDIVAS_precomputed/GRCh38/PDIVAS_precomputed_short_GRCh38.vcf.gz"
# ID and FILTER are special fields that pull the ID and FILTER columns from the VCF
fields = ["PDIVAS"]
ops=["self"]
names=["PDIVAS"]
[[annotation]]
file="cadd_precomputed_snv.tsv.gz"
names=["cadd_raw", "cadd_phred"]
ops=["mean", "mean"]
columns=[4, 5]
```

Annotate VCF files from `4_pangolin` folder:
```bash
mkdir 5_cadd_pdivas;
cd 5_cadd_pdivas;
for file in ../4_pangolin/*vcf; do \
name=`basename $file`; \
vcfanno -p 12 ann.conf $file > ${name%vcf}cadd.pdivas.vcf; \
done;
```
