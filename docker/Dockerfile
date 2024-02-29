# Use the Ubuntu base image
FROM quay.io/bedrock/ubuntu

# Update package lists
RUN apt-get update

# Install any desired packages
# For example, installing curl
RUN apt-get install -y curl
RUN apt-get update && apt-get install -y git 
RUN apt-get install -y git-svn
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        python3 \
        python3-pip \
    && rm -rf /var/lib/apt/lists/*
# Set the working directory
WORKDIR /app

# Add your application files
# For example, copy a script into the image
COPY . .
COPY script.sh .
# Set the working directory
WORKDIR /app
COPY . .
# Copy your application files into the container
COPY . /app

# Install Python dependencies
RUN pip3 install --no-cache-dir -r requirements.txt

# Expose the port on which your application runs
EXPOSE 8080

# Specify the command to run your application
CMD ["python3", "app.py"]
