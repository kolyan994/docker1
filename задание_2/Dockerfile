
FROM python:3.10


WORKDIR /app

COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt


COPY . /app/


ENV DJANGO_SETTINGS_MODULE=stocks_products.settings
ENV PYTHONUNBUFFERED=1


RUN python manage.py migrate
RUN python manage.py collectstatic --noinput


EXPOSE 8000


CMD ["gunicorn", "--bind", "0.0.0.0:8000", "stocks_products.wsgi:application"]