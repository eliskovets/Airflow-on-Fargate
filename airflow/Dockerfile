#FROM apache/airflow:2.3.4-python3.7 # amd64
FROM apache/airflow@sha256:2c685ae498a10b4c9ad06db92dd6dc9eb4a6bf5a6d536608249853d5343bd3c5

ENV AIRFLOW_HOME=/usr/local/airflow

USER root

RUN apt-get update && apt-get install -y \
    gcc \
    libcurl4-gnutls-dev \
    librtmp-dev \
    libpq-dev

COPY ./config/* /
COPY ./dags ${AIRFLOW_HOME}/dags

RUN chown -R airflow: ${AIRFLOW_HOME}

EXPOSE 8080

USER airflow

RUN python3 -m pip install PyGreSQL argcomplete pycurl pgdb celery boto3 'apache-airflow[amazon]'

WORKDIR ${AIRFLOW_HOME}

# ENTRYPOINT ["/entrypoint.sh"]
