ARG PYTHON_VERSION=3.9-slim-buster
FROM python:${PYTHON_VERSION} as python

# Python build stage
FROM python as python-build-stage

ENV LISTEN_PORT=6000
EXPOSE 6000:6000

# Install apt packages
RUN apt-get update && apt-get install --no-install-recommends -y \
  # dependencies for building Python packages
  build-essential \
  # psycopg2 dependencies
  libpq-dev
  
RUN pip install --pre flask flask-restful numpy pandas requests darts requests numpy tqdm schedule tensorflow pandas psutil h5py h5_to_json keras
WORKDIR /usr/src/app
COPY . .

CMD [ "python", "-m" , "flask", "--app=demoEdgeNode", "--debug", "run", "--host=0.0.0.0"]

