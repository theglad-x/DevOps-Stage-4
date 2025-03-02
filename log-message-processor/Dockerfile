# Base image
FROM python:3.9

#working directory
WORKDIR /app

# Copy requirement.txt file and install dependencies
COPY requirements.txt .

# Install dependencies, excluding py_zipkin
RUN grep -v "py_zipkin" requirements.txt | pip install -r /dev/stdin

# Install py_zipkin v0.20.0 explicitly
RUN pip install py_zipkin==0.20.0

# Copy application code
COPY . .

# Run the application
CMD ["python3", "main.py"]
