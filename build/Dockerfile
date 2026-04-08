ARG JFROG_BASE_REPOSITORY
ARG JFROG_URL

FROM $JFROG_URL/$JFROG_BASE_REPOSITORY/privacy/python:3.18

RUN --mount=type=secret,id=_env,dst=/etc/secrets/.env . /etc/secrets/.env \
    && pip install $PIP_INDEX_URL ray[default] tensorboardX boto3

ARG JFROG_BASE_REPOSITORY
ARG JFROG_URL
FROM $JFROG_URL/$JFROG_BASE_REPOSITORY/privacy/python:3.18

COPY build/requirements.txt .
RUN pip install -r requirements.txt

WORKDIR /app
COPY ./src ./src
COPY main.py .
