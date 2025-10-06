# [SQUIRLS](https://github.com/monarch-initiative/Squirls) annotation

To annotate VCF files with SQUIRLS we used following command

```bash
for file in 3_spliceai/*vcf; do \
name=`basename $file`; \
java -jar squirls-cli-2.0.1.jar annotate-vcf -d GRCh38.fa --output-format vcf \
--out-dir 4_squirls $file 4_squirls/${name%vcf}squirls.vcf; \
done;
```
