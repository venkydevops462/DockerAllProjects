# Step 1: Use a lightweight Python image to build the application
FROM python:3.10-slim AS builder

# Install Flask
RUN pip install Flask

# Copy application files
WORKDIR /app
COPY app.py .

# Step 2: Copy only necessary files into the Distroless image
FROM gcr.io/distroless/python3

# Copy the dependencies and app files from builder stage
COPY --from=builder /usr/local/lib/python3.10 /usr/local/lib/python3.10
COPY --from=builder /app /app

# Set working directory and entry point
WORKDIR /app
EXPOSE 8080
ENTRYPOINT ["python3", "app.py"]
