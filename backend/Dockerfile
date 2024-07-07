# Dockerfile for FastAPI Backend with Poetry

FROM python:3.10-slim

# Set the working directory
WORKDIR /app

# Install Poetry
RUN apt-get update && apt-get install -y curl
RUN curl -sSL https://install.python-poetry.org | python3 -
ENV PATH="/root/.local/bin:$PATH"

# Copy only the necessary files
COPY pyproject.toml poetry.lock /app/

# Set PYTHONPATH environment variable
ENV PYTHONPATH=/app

# Install dependencies
RUN poetry install

# Copy the rest of the application
COPY . /app

# Set PYTHONPATH environment variable again, just in case
ENV PYTHONPATH=/app

# Ensure prestart script is executable
RUN chmod +x /app/prestart.sh

# Expose port that FastAPI will run on
EXPOSE 8000

# run prestart script and start the application
CMD ["bash", "-c", "poetry run bash ./prestart.sh && poetry run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000"]
