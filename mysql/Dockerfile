# Tking official docker image of mysql:8.0 version in docker hub.
FROM mysql:8.0

# setting up mysql root passord
ENV MYSQL_ROOT_PASSWORD=RoboShop@1

#I copy SQL initialization scripts into /docker-entrypoint-initdb.d/, a directory supported by the official MySQL image. The entrypoint executes those scripts when the database is initialized for the first time, allowing us to automate database schema creation and initial data loading.
#When a container is started for the first time, a new database with the specified name will be created and initialized with the provided configuration variables. Furthermore, it will execute files with extensions .sh, .sql, .sql.gz, .sql.bz2, .sql.xz, and .sql.zst that are found in /docker-entrypoint-initdb.d. Files will be executed in alphabetical order. When parsing .sh files without the execute bit set, they are sourced rather than executed.
COPY db/* /docker-entrypoint-initdb.d/