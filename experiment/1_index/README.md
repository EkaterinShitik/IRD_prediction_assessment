# Indexing and sorting

For further steps VCF must be sorted and have appropriate indexes in the header. For sorting and indexing we use bcftools. In our workflow we used GRCh38 human genome assembly(you can download it with VEP installer, see next step).

```bash
for file in 0_init/*vcf; do \
name=`basename $file`; \
bcftools reheader --fai GRCh38.fa.fai $file | \
bcftools sort -o ${name%.vcf}_indexed.vcf; \
done
```
