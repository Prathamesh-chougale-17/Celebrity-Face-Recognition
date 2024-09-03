# Use the official Python image as the base image
FROM python:3.8-slim

# Install necessary system packages for libGL and other dependencies
RUN apt-get update && apt-get install -y \
    libgl1-mesa-glx \
    libglib2.0-0 \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file to the container
COPY requirements.txt .

# Install Python dependencies
RUN python -m venv venv \
    && . venv/bin/activate \
    && pip install --upgrade pip \
    && pip install -r requirements.txt

# Copy the rest of the application code to the container
COPY . .

# Expose the port that Flask runs on
EXPOSE 5000

# Run the Flask application
CMD ["venv/bin/python", "server.py"]
