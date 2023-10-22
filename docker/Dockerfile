FROM jupyter/datascience-notebook:python-3.9.13
#FROM jupyter/datascience-notebook:python-3.10.6
#FROM jupyter/datascience-notebook:python-3.8.6

#RUN conda config --remove channels defaults
#既に入ってなかった
#RUN conda config --append channels conda-forge
#既に入ってた
#RUN conda config --set channel_priority strict

RUN conda update -n base conda

#依存関係のせいか後半でインストールしようとしたら1日待っても入らなかったので最初のほうに入れてみる
RUN conda install -c conda-forge geopandas

RUN jupyter server extension disable nbclassic

RUN conda install --yes -c conda-forge ipywidgets
RUN conda install --yes -c conda-forge ipympl
RUN conda install --yes -c conda-forge nodejs

RUN jupyter labextension install @jupyter-widgets/jupyterlab-manager
RUN jupyter labextension install jupyter-matplotlib

RUN conda install --yes -c conda-forge openpyxl

RUN conda install -c conda-forge sentinelsat
#sentinelsat license GPL3

RUN conda install -c conda-forge folium
RUN conda install -c conda-forge rasterio
RUN conda install -c conda-forge gdal
RUN conda install -c conda-forge opencv

RUN conda install -c conda-forge mkl-service
RUN conda install -c conda-forge arviz==0.11.1
RUN conda install -c conda-forge numpy==1.21
RUN conda install -c conda-forge pymc3
# RUN conda install -c conda-forge pymysql

RUN conda install -c conda-forge jupytext
RUN echo 'c.ContentsManager.default_jupytext_formats = "ipynb,py"' >> \
  /home/jovyan/.jupyter/jupyter_notebook_config.py

RUN conda install -y -c conda-forge rioxarray

RUN conda install -y -c conda-forge beautifulsoup4
RUN conda install -y -c conda-forge lxml

RUN conda clean --all -f -y

RUN curl -L  "https://moji.or.jp/wp-content/ipafont/IPAexfont/IPAexfont00401.zip" > font.zip
RUN unzip font.zip
RUN cp IPAexfont00401/ipaexg.ttf /opt/conda/lib/python3.9/site-packages/matplotlib/mpl-data/fonts/ttf/ipaexg.ttf
RUN rm -r IPAexfont00401
RUN rm font.zip
RUN echo "font.family : IPAexGothic" >> /opt/conda/lib/python3.9/site-packages/matplotlib/mpl-data/matplotlibrc
RUN rm -r ./.cache
