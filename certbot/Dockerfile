########################################################################
FROM snakepacker/python:all as certbot-builder

RUN python3.7 -m venv /usr/share/python3/app

RUN /usr/share/python3/app/bin/pip install -U pip 'certbot'

########################################################################
FROM snakepacker/python:3.7

COPY --from=certbot-builder /usr/share/python3/app /usr/share/python3/app
RUN ln -snf /usr/share/python3/app/bin/certbot /usr/bin/

VOLUME /etc/letsencrypt /var/lib/letsencrypt
EXPOSE 80 443

ENTRYPOINT [ "certbot" ]
########################################################################