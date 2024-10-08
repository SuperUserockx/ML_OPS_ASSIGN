# Use a lightweight Python image
FROM python:3.9-slim

# Set the working directory
WORKDIR /workspace

# Copy all project files into the container
COPY . .

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libssl-dev \
    libffi-dev \
    python3-dev

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose port 80 (optional)
EXPOSE 80

# Set an environment variable (optional)
ENV NAME MLOpsLab

# Define the default command to run the training script
CMD ["python", "train.py"]
