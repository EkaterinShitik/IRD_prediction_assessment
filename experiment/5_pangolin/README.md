# [Pangolin](https://github.com/tkzeng/Pangolin) annotation

To annotate VCF files with Pangolin we used following command

```bash
for file in 4_squirls/*vcf; do \
name=`basename $file`; \
pangolin -d 100 $file GRCh38.fa gencode.v38.annotation.db 5_pangolin/${name%vcf}pangolin.vcf; \
done;
```
