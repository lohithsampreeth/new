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

# Create a new user and group with the same name 'user'
RUN groupadd -r user && useradd -r -g user user

# Set the working directory
WORKDIR /app

# Add your application files
# For example, copy a script into the image
COPY . .
COPY script.sh .

# Copy your application files into the container
COPY . /app

# Install Python dependencies
RUN pip3 install --no-cache-dir -r requirements.txt

# Expose the port on which your application runs
EXPOSE 8080

# Change the ownership of the application directory to the newly created user
RUN chown -R user:user /app

# Specify the command to run your application
USER user
CMD ["python3", "app.py"]
