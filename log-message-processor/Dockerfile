# Base image
FROM python:3.9

#working directory
WORKDIR /app

# Copy requirement.txt file and install dependencies
COPY requirements.txt .

RUN pip3 install --no-cache-dir --upgrade pip \
    && pip3 install --no-cache-dir -r requirements.txt
# Copy application code
COPY . .

# Run the application
CMD ["python3", "main.py"]
