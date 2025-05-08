# set base image (host OS)
FROM python:3.8

# set the working directory in the container
WORKDIR /code

# copy the dependencies file to the working directory
COPY . .

# install dependencies
RUN pip install --upgrade pip && \
    pip install -r requirements.txt

RUN opentelemetry-bootstrap --action=install

# command to run on container start: 
# ejecuta la app y redirige stdout y stderr al archivo /code/app.log
CMD ["sh", "-c", "opentelemetry-instrument python -u app.py 2>&1 | tee -a /code/app.log"]

# expose port
EXPOSE 5002

