# Use the Ubuntu base image
FROM ubuntu:latest

# Update package lists
RUN apt-get update

# Install any desired packages
# For example, installing curl
RUN apt-get install -y curl
RUN apt-get update && apt-get install -y git 
RUN apt-get install -y git-svn
# Set the working directory
WORKDIR /app

# Add your application files
# For example, copy a script into the image
COPY . .
COPY script.sh .

# Set permissions if needed
# RUN chmod +x script.sh

# Define the command to run when the container starts
CMD ["/bin/bash", "./script.sh"]
