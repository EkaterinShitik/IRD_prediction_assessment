# [SPiP](https://github.com/LBGC-CFB/SPiP) annotation

1. Clone SPiP repo
```bash
git clone https://github.com/raphaelleman/SPiP;
```
2. Download SPiP reference data manually - [hg38.Rdata](https://sourceforge.net/projects/splicing-prediction-pipeline/files/transcriptome/transcriptome_hg38.RData)
```bash
mv  transcriptome_hg38.RData SPiP/RefFiles
```
3. Install needed R packages in your SPiP environment
```R
install.packages("foreach")
install.packages("doParallel")
install.packages("randomForest")
```

Annotate files from `5_cadd_pdivas_precomputed`:
```bash
mkdir 6_spip;
cd 6_spip;
for file in ../5_cadd_pdivas/*vcf; do \
name=`basename $file`; \
Rscript ../SPiP/SPiPv2.1_main.r -t 12 --VCF --verbose -g hg38 -I $file -O ${name%vcf}spip.vcf; \
done;
```
