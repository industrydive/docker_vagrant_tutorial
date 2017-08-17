FROM ubuntu:16.04

RUN rm /bin/sh && ln -s /bin/bash /bin/sh
RUN apt-get update && apt-get install -y build-essential \
    python3 \
    python3-dev \
    python3-pip

RUN pip3 install virtualenv virtualenvwrapper
RUN mkdir $HOME/.virtualenvs
ENV VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
ENV WORKON_HOME=$HOME/.virtualenvs

RUN echo "source /usr/local/bin/virtualenvwrapper.sh && workon tutorial" >> $HOME/.bashrc

COPY requirements.txt requirements.txt

RUN source /usr/local/bin/virtualenvwrapper.sh && mkvirtualenv tutorial && workon tutorial && pip3 install -r requirements.txt

VOLUME /srv/www
WORKDIR /srv/www

RUN mkdir -p /srv/uwsgi
COPY uwsgi.ini /srv/uwsgi/

# CMD ["/bin/sleep", "Inf"]
CMD source /usr/local/bin/virtualenvwrapper.sh && workon tutorial && uwsgi --ini /srv/uwsgi/uwsgi.ini
