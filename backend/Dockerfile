# Dockerfile for FastAPI Backend with Poetry

FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 -
ENV PATH="/root/.local/bin:$PATH"

# Copy only the necessary files
COPY pyproject.toml poetry.lock /app/

# Install dependencies
RUN poetry install --no-root

# Copy the rest of the application
COPY . /app

# Ensure prestart script is executable
RUN chmod +x /app/prestart.sh

# Entry point to run prestart script and start the application
ENTRYPOINT ["poetry", "run", "bash", "-c", "/app/prestart.sh && uvicorn app.main:app --host 0.0.0.0 --port 8000"]
