# bioinformatics_docker_files

## Docker files for building bioinformatics working environments

- Each folder contains a Dockerfile
- ```cd``` into that folder to build
- ```cd``` into a bioinformatics project root to use

### transcript_quant_go_mouse
- Jupyter notebook environment with Python and R kernels
- trim_galore, salmon, tximport, DESeq2, goseq, gprofiler2, mouse annotations

```
docker build -t transcript_quant_go_mouse .
docker run --rm -it -p 8888:8888 -v `pwd`:/work transcript_quant_go_mouse
```

### rna_seq_splice_align_view
- Jupyter notebook environment with Python kernel
- trim_galore, star, minimap2, samtools, igv

```
docker build -t rna_seq_splice_align_view .
docker run --rm -it -p 8888:8888 -v `pwd`:/work rna_seq_splice_align_view
```

### braker2
- Jupyter notebook environment with Python kernel
- trim_galore, hisat2, samtools, braker2
- add licence file ```gm_key_64.gz``` into directory with ```Dockerfile```
- change ```Dockerfile``` Genemark download link (###Genemark Link###) as required 

```
docker build -t braker2 .
docker run --rm -it -p 8888:8888 -v `pwd`:/work braker2
```
