FROM python:3.11-alpine

WORKDIR /usr/src/app

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1


COPY ./requirements.txt .
RUN pip install --upgrade pip \
    && pip install -r requirements.txt

COPY entrypoint.sh .
RUN sed -i 's/\r$//g' /usr/src/app/entrypoint.sh
RUN chmod +x /usr/src/app/entrypoint.sh

COPY . .

ENTRYPOINT [ "/usr/src/app/entrypoint.sh" ]
#RUN python manage.py collectstatic --noinput

#CMD ["gunicorn", "myproject.wsgi:application", "--bind", "0.0.0.0:8000"]
