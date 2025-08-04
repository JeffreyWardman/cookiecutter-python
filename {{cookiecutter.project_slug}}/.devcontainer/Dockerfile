FROM python:3.13-slim

# Install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/uv

WORKDIR /app

# Install dependencies
COPY uv.lock /app/uv.lock
COPY pyproject.toml /app/pyproject.toml
RUN uv sync --frozen --no-install-project

# Copy the project into the image
COPY . /app

# Sync the project
RUN uv sync --frozen

ENTRYPOINT ["uv", "run"]
CMD ["python"]
