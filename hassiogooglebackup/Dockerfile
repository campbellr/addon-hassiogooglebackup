ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Install requirements for add-on
RUN apk add --no-cache \
    jq \
  && rm -rf /var/cache/apk/*

COPY googlebackup /googlebackup

RUN pip install -r googlebackup/requirements.txt \
  && cd googlebackup \
  && python manage.py migrate

# Copy data for add-on
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
