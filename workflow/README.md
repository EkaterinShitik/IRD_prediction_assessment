# Workflow steps

Folders store VCF files at a particular stage of processing and the commands used to get them. 

The final files processed with VETA are stored in `final` and have been analysed in the `Data_analysis` notebook.

To replicate our work start with environments creation([conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)/[mamba](https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html)):
```bash
mamba env create -f environment.yaml
```
