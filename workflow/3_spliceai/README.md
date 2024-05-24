# [SpliceAI](https://github.com/Illumina/SpliceAI.git) annotation
1. Install SpliceAI via pip or conda
```bash
pip install spliceai
# or
conda install -c bioconda spliceai
```
Additionally you should install `tensorflow>=1.2.0`
```bash
pip install tensorflow
# or
conda install tensorflow
```
2. Download reference file [GRCh37/hg19](http://hgdownload.cse.ucsc.edu/goldenPath/hg19/bigZips/hg19.fa.gz) or [GRCh38/hg38](http://hgdownload.cse.ucsc.edu/goldenPath/hg38/bigZips/hg38.fa.gz)
3. Annotate files from `2_vep_maxentscan` folder:
```bash
for file in ../2_vep_maxentscan/*vcf; do \
name=`basename $file`; \
spliceai -I $file -O ${name%vcf}sai.vcf -D 100 -R GRCh38.primary_assembly.genome.fa -A grch38; \
done;
```
