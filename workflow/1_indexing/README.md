# Indexing and sorting 

For further steps VCF must be sorted and have appropriate indexes in the header. For sorting and indexing we use bcftools. In our workflow we used GRCh38 human genome assembly(you can download it with VEP installer, see next step).

```bash
for file in ../init/*vcf; do \
name=`basename $file`; \
bcftools reheader \
--fai ../ensembl-vep/vep_cache/homo_sapiens/111_GRCh38/Homo_sapiens.GRCh38.dna.toplevel.fa.gz.fai \ # path to GRCh38
$file | bcftools sort -o ${name%.vcf}_indexed.vcf; \
done;
```