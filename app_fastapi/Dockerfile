FROM python:3.11-slim

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt && \
    opentelemetry-bootstrap -a install

EXPOSE 8000

ENV TARGET_ONE_SVC=fastapi:8080 \
    TARGET_TWO_SVC=fastapi:8080 \
    OTEL_TRACES_EXPORTER=otlp \
    OTEL_EXPORTER_OTLP_ENDPOINT=http://otel-collector:4317 \
    OTEL_METRICS_EXPORTER=none \
    OTEL_SERVICE_NAME=fastapi

# Define the command to run the application
CMD ["opentelemetry-instrument", "python", "main.py"]