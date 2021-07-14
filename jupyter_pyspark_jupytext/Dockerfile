ARG BASE_CONTAINER=jupyter/pyspark-notebook
FROM $BASE_CONTAINER
RUN echo $USER

# Instalar paqueterías adicionales
RUN pip install jupytext --upgrade
RUN pip install python-dotenv


# Instalar tema dracula
RUN jupyter labextension install @telamonian/theme-darcula --no-build

# Construir Jupyter Lab
RUN jupyter lab build

# Extensión de Jupytext y activar la extension para los notebooks
RUN jupyter serverextension enable jupytext

# Asignar contraseña del notebook como rafaelortegar
RUN sed -i "s/#c.NotebookApp.password = .*/c.NotebookApp.password = u'sha1:8437d0b83ce5:6b7b935c40c5ea96ab2b20378e0797c9f46b2a0d'/" ~/.jupyter/jupyter_notebook_config.py

# Añadir linea para que pueda funcionar jupytext
RUN echo 'c.NotebookApp.contents_manager_class = "jupytext.TextFileContentsManager"' >> ~/.jupyter/jupyter_notebook_config.py


USER $NB_UID

WORKDIR $HOME

EXPOSE 8888

EXPOSE 4040

LABEL org.opencontainers.image.authors="rafaelortegar"
LABEL version="0.0.1"
LABEL description="This docker image contains pyspark, jupyter, jupytext"



#docker run --name <nombre> -d \
#    -p 8888:8888 -p 4040:4040 \
#    -e JUPYTER_ENABLE_LAB=yes -e RESTARTABLE=yes -e GRANT_SUDO=yes \
#    -e NB_UID=$(id -u) -e NB_GID=$(id -g) \
#    --user root \
#    -v "$HOME/Documents":/home/jovyan/work \
#    jupyter/<imagen>