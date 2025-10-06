# [SpliceAI](https://github.com/Illumina/SpliceAI.git) annotation

SpliceAI was installed via [Dockerfile](https://github.com/apaul7/docker-splice-ai/blob/master/Dockerfile). To annotate VCF files with SpliceAI we used following command

```bash
for file in 2_vep/*vcf; do \
name=`basename $file`; \
docker run -it -u $USER_ID:$GROUP_ID \
-v ./2_vep:/input -v ./3_spliceai:/output -v ../hg38:/fa \
spliceai spliceai -R /fa/genome_noprefix.fa -A grch38 -I /input/$file -O /output/${name%vcf}sai.vcf -D 100 ; \
done
```
