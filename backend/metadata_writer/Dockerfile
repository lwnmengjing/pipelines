# ml-metadata package depends on tensorflow package
FROM python:3.8

RUN python3 -m pip install --upgrade pip
RUN python3 -m pip install tensorflow==2.13.1
RUN python3 -m pip install tensorflow-metadata
RUN python3 -m pip install tensorflow-metadata-store
COPY backend/metadata_writer/requirements.txt /kfp/metadata_writer/
RUN python3 -m pip install -r /kfp/metadata_writer/requirements.txt

COPY backend/metadata_writer/src/* /kfp/metadata_writer/
CMD python3 -u /kfp/metadata_writer/metadata_writer.py
