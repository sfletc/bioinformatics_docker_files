# bioinformatics_docker_files

## Docker files for building bioinformatics working environments

### transcript_quant_go_mouse
- Jupyter notebook environment with Python and R kernels
- trim_galore, salmon, tximport, DESeq2, goseq, mouse annotations

```
docker build -t transcript_quant_go_mouse .
docker run --rm -it -p 8888:8888 -v `pwd`:/work transcript_quant_go_mouse
```
