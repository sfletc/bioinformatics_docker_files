# bioinformatics_docker_files

## Docker files for building bioinformatics working environments

- Each folder contains a Dockerfile
- ```cd``` into that folder to build
- ```cd``` into a bioinformatics project root to use

### transcript_quant_go_mouse
- Jupyter notebook environment with Python and R kernels
- trim_galore, salmon, tximport, DESeq2, goseq, mouse annotations

```
docker build -t transcript_quant_go_mouse .
docker run --rm -it -p 8888:8888 -v `pwd`:/work transcript_quant_go_mouse
```

### rna_seq_splice_align_view
- Jupyter notebook environment with Python kernel
- trim_galore, star, minimap2, samtools, igv

