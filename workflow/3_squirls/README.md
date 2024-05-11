# [SQUIRLS](https://github.com/monarch-initiative/Squirls) annotation
1. Download the [tool](https://github.com/monarch-initiative/Squirls/releases/tag/v2.0.1). To find the program, open the directory
```bash
cd squirls-cli-2.0.1
``` 

2. Download the reference [hg38/GRCh38 database](https://storage.googleapis.com/squirls/2203_hg38.zip)

3. Annotate files from `2_cis` folder:
```bash
mkdir 3_squirls;
cd 3_squirls;
for file in ../2_cis/*vcf; do \
name=`basename $file`; \
java -jar <full path>/squirls-cli-2.0.1.jar annotate-vcf -d <full path>/2203_hg38 --output-format vcf \
--out-dir . $file ${name%vcf}squirls; \
done;
```
