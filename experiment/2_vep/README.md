# [VEP](https://www.ensembl.org/info/docs/tools/vep/index.html) annotation

To annotate VCF files with VEP we used following command

```bash
for file in 1_index/*vcf; do \
file=`basename $file`; \
docker run -u $USER_ID:$GROUP_ID -it \
-v ../hg38/:/fa -v ./1_index:/input -v ./2_vep:/output -v $HOME/.vep:/data \
ensemblorg/ensembl-vep vep \
--cache  --dir_cache /data --assembly GRCh38 --offline \
--fasta /fa/genome_noprefix.fa \
--hgvs --pick_allele_gene --vcf --fields "Consequence,SYMBOL,Gene,INTRON,HGVSc,STRAND" \
-i /input/$file -o /output/${file%vcf}vep.vcf; \
done
```

