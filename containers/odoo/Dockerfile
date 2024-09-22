FROM quay.io/acsone/odoo-bedrock:12.0-py35-latest

RUN set -e \
  && apt-get -f install \
  && apt-get install -y --no-install-recommends

RUN echo 'deb http://apt.postgresql.org/pub/repos/apt/ bullseye-pgdg main' > /etc/apt/sources.list.d/pgdg.list 

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
  && rm -f /etc/apt/sources.list.d/pgdg.list \
  && rm -rf /var/lib/apt/lists/* \
  && apt -y clean 

COPY ./entrypoint-db /odoo/start-entrypoint.d/

COPY ./requirements.txt /tmp/

RUN pip install -r /tmp/requirements.txt

