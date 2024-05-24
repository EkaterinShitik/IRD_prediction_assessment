# [SQUIRLS](https://github.com/monarch-initiative/Squirls) annotation
1. Download the [tool](https://github.com/monarch-initiative/Squirls/releases/tag/v2.0.1). To find the program, open the directory
```bash
cd squirls-cli-2.0.1
``` 

2. To download the reference database visit the [website](https://squirls.readthedocs.io/en/latest/setup.html)

3. Annotate files from `4_cis` folder:
```bash
for file in ../4_cis/*vcf; do \
name=`basename $file`; \
java -jar <full path>/squirls-cli-2.0.1.jar annotate-vcf -d <full path>/2203_hg38 --output-format vcf \
--out-dir . $file ${name%vcf}squirls; \
done;
```
