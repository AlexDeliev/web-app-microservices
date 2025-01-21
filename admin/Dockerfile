FROM python:3.12-slim-bullseye

# Install system dependencies for Python packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    pkg-config \
    libmariadb-dev \
    gcc \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt /app/

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the entire application into the container
COPY . /app

# Expose the application port
EXPOSE 8000

# Default command to run the application
CMD [ "python3", "manage.py", "runserver", "0.0.0.0:8000" ]