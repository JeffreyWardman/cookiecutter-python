FROM python:3.10

# Install poetry
ENV POETRY_HOME=/opt/poetry
RUN python3 -m venv $POETRY_HOME && $POETRY_HOME/bin/pip install poetry==1.6.1
ENV PATH="$POETRY_HOME/bin:$PATH"
COPY . /app
WORKDIR /app

RUN apt-get -y update && \
    apt-get install -y --no-install-recommends \
    libgl1-mesa-glx && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean
RUN poetry install

ENV SHELL=/bin/bash

ENTRYPOINT ["poetry", "run"]
CMD ["python"]