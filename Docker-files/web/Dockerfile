# Use the latest Nginx image as the base image
FROM nginx:latest

# Add metadata to the image
LABEL Project="Vprofile"
LABEL Author="Yana"

# Remove the default Nginx configuration file
# The -f flag ensures that no error is thrown if the file does not exist
RUN rm -f /etc/nginx/conf.d/default.conf

# Copy the custom Nginx configuration file into the container
# Ensure the file 'nginvproapp.conf' exists in the same directory as this Dockerfile
COPY nginvproapp.conf /etc/nginx/conf.d/vproapp.conf
