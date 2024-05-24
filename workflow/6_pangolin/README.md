# [Pangolin](https://github.com/tkzeng/Pangolin) annotation
1. Install Pangolin via conda and pip
```bash
conda install -c conda-forge pyvcf
pip install gffutils biopython pandas pyfastx
```
Clone repository 
```bash
git clone https://github.com/tkzeng/Pangolin.git
cd Pangolin
pip install .
```
To set up GPU install [PyTorch](https://pytorch.org/get-started/locally/)

2. Download reference genome assembly [GRCh38/hg38](http://hgdownload.cse.ucsc.edu/goldenPath/hg38/bigZips/hg38.fa.gz). *Or use from the previous `3_spliceai` directory.*

Download reference database 
```bash
# download annotation file
wget https://www.dropbox.com/sh/6zo0aegoalvgd9f/AADOhGYJo8tbUhpscp3wSFj6a/gencode.v38.annotation.db
```
3. Annotate files from `5_squirls` folder:
```bash
for file in ../5_squirls/*vcf; do \
name=`basename $file`; \
pangolin -d 100 $file GRCh38.primary_assembly.genome.fa gencode.v38.annotation.db ${name%vcf}pangolin;
done;
```
