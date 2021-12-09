FROM python:3.8-slim
WORKDIR /app
ENV PYTHONBUFFERED 1
COPY lib_catalog/ /app
RUN apt-get update \
    && apt-get install -y --no-install-recommends postgresql-client curl\
    && rm -rf /var/lib/apt/lists/* \
    && pip3 install django \
    && pip3 install -r requirements.txt \ 
    && sed -i 's/ALLOWED_HOSTS = \[\]/ALLOWED_HOSTS = \["*"\]/g' /app/lib_catalog/settings.py  \
    && echo "\nCORS_ORIGIN_ALLOW_ALL = True" >> /app/lib_catalog/settings.py
ENTRYPOINT ["python", "manage.py", "runserver"]