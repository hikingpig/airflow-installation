# install docker on Mac M1
https://docs.docker.com/desktop/mac/apple-silicon/

# starts and log-in Docker
- open Docker in launch pad
- log-in with email and password
- keep it open

# start an airflow container:
```sh
docker run -ti --platform linux/amd64 -p 8080:8080 -v /Users/phuocphi/HCL/data-pipelines-with-apache-airflow-master/chapter02/dags/download_rocket_launches.py:/opt/airflow/dags/download_rocket_launches.py --entrypoint=/bin/bash --name airflow apache/airflow:2.0.0-python3.8 -c '(\
airflow db init && \
airflow users create --username admin --password admin --firstname Anonymous --lastname Admin --role Admin --email admin@example.org \
); \
airflow webserver & \
airflow scheduler \
'
```
- the line `--platform linux/amd64` is to suppress a WARNING. Docker works just fine without it.

# check the result by seeing downloaded images in /tmp folder of the container
docker exec -it airflow /bin/bash