# Pasos para construir la imagen

## Build

```bash
docker build -f Dockerfile --rm -t rafaelortegar/jupytext_pyspark:0.0.1 -t rafaelortegar/jupytext_pyspark:latest
```

## Run

```bash
docker run --name jupytext_pyspark -d \
        -p 8888:8888 -p 4040:4040 \
        -e JUPYTER_ENABLE_LAB=yes -e RESTARTABLE=yes -e GRANT_SUDO=yes \
        -e NB_UID=$(id -u) -e NB_GID=$(id -g) \
        --user root \
        -v "$HOME/Documents":/home/jovyan/work \
        rafaelortegar/jupytext_pyspark:latest
```
