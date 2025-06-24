FROM python:3.13-rc-slim

# Install uv globally
RUN apt-get update && apt-get install -y curl && pip install uv

WORKDIR /app

# Copy dependency files
COPY pyproject.toml uv.lock ./

# Create venv and install inside it using global uv
RUN uv venv && \
    uv pip install .  

# Copy source code
COPY app.py ./

# Activate venv for container
ENV PATH="/app/.venv/bin:$PATH"

EXPOSE 8002

CMD ["python", "app.py"]