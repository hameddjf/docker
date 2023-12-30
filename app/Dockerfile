FROM python:alpine

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV DJANGO_SUPERUSER_PASSWORD admin

RUN mkdir /app
WORKDIR /app

RUN pip install --upgrade pip
RUN pip install django waitress
CMD python3 manage.py makemigrations --noinput && \
    python3 manage.py migrate --noinput && \
    python manage.py collectstatic --noinput && \
    python3 manage.py createsuperuser --user hamed --email hameddjf33@gmail.com --noinput; \
    waitress-serve --listen=*:8000 config.wsgi:application