# Use the latest version of the Amazon Linux base image
FROM amazonlinux:2023

# Update all installed packages to thier latest versions
RUN yum update -y 

# Install the unzip package, which we will use it to extract the web files from the zip folder
RUN yum install unzip -y

# Install wget package, which we will use it to download files from the internet 
RUN yum install -y wget

# Install PHP 8.0 and required extensions
RUN dnf install -y httpd wget php-fpm php-mysqli php-json php php-devel

# Copy custom php.ini to enable the cURL module
COPY php.ini /etc/php.ini



# Copy custom php.ini with updated settings
COPY php.ini /usr/local/etc/php/

# Install required packages
RUN dnf install -y wget

# Download MySQL repository package
RUN wget https://dev.mysql.com/get/mysql80-community-release-el9-1.noarch.rpm

# List downloaded file
RUN ls -lrt

# Install MySQL repository package
RUN dnf install -y mysql80-community-release-el9-1.noarch.rpm

# Install MySQL Community Server
RUN dnf install -y mysql-community-server

# Change directory to the html directory
WORKDIR /var/www/html

# Install Git
RUN yum install -y git

# Clone the GitHub repository
RUN git clone https://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@github.com/werkmanne/docker-project-app-codes.git

WORKDIR /var/www/html/docker-project-app-codes

RUN unzip nest-app.zip -d docker-project-app-codes/

# RUN ls -la

# # Unzip the zip folder containing the web files
# RUN unzip werkmanne/nest-app.zip -d docker-project-app-codes/



# # Copy the web files into the HTML directory
# RUN cp -av $REPOSITORY_NAME/$WEB_FILE_UNZIP/. /var/www/html

# # Remove the repository we cloned
# RUN rm -rf $REPOSITORY_NAME

# # Enable the mod_rewrite setting in the httpd.conf file
# RUN sed -i '/<Directory "\/var\/www\/html">/,/<\/Directory>/ s/AllowOverride None/AllowOverride All/' /etc/httpd/conf/httpd.conf

# # Give full access to the /var/www/html directory
# RUN chmod -R 777 /var/www/html

# # Give full access to the storage directory
# RUN chmod -R 777 storage/

# # Use the sed command to search the .env file for a line that starts with APP_ENV= and replace everything after the = character
# RUN sed -i '/^APP_ENV=/ s/=.*$/=production/' .env

# # Use the sed command to search the .env file for a line that starts with APP_URL= and replace everything after the = character
# RUN sed -i "/^APP_URL=/ s/=.*$/=https:\/\/$DOMAIN_NAME\//" .env

# # Use the sed command to search the .env file for a line that starts with DB_HOST= and replace everything after the = character
# RUN sed -i "/^DB_HOST=/ s/=.*$/=$RDS_ENDPOINT/" .env

# # Use the sed command to search the .env file for a line that starts with DB_DATABASE= and replace everything after the = character
# RUN sed -i "/^DB_DATABASE=/ s/=.*$/=$RDS_DB_NAME/" .env 

# # Use the sed command to search the .env file for a line that starts with DB_USERNAME= and replace everything after the = character
# RUN  sed -i "/^DB_USERNAME=/ s/=.*$/=$RDS_MASTER_USERNAME/" .env

# # Use the sed command to search the .env file for a line that starts with DB_PASSWORD= and replace everything after the = character
# RUN  sed -i "/^DB_PASSWORD=/ s/=.*$/=$RDS_DB_PASSWORD/" .env

# # Copy the file, AppServiceProvider.php from the host file system into the container at the path app/Providers/AppServiceProvider.php
# COPY AppServiceProvider.php app/Providers/AppServiceProvider.php

# # Expose the default Apache and MySQL ports
# EXPOSE 80 3306

# # Start Apache and MySQL
# ENTRYPOINT ["/usr/sbin/httpd", "-D", "FOREGROUND"]