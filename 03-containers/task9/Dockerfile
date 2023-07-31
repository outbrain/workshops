FROM python:alpine

# Requirements are copied, and hash of the file is recorded. Only when the hash
# changes will this layer be updated!
COPY requirements.txt /tmp/requirements.txt
RUN pip install -r /tmp/requirements.txt

COPY ./src /src
WORKDIR /src

CMD gunicorn --bind 0.0.0.0:5000 --workers 10 counter:app
EXPOSE 5000