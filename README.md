# wordpress
we can create the wordpress to use of docker first we can two files one is mysql docker file and another one is wordpress docker file then exicute the files.
docker build -t custom_mysql_image .
docker build -t custom_wp_img .
docker run --name mysql_container custom_mysql_image(when you dont give any extra parameters and use paramenters as in dcokerfile)
For custom parameters
docker run -d
--name mysql-container
-v mysql_data:/var/lib/mysql
-e MYSQL_ROOT_PASSWORD=root_password
-e MYSQL_DATABASE=wp_db
-e MYSQL_USER=wp_user
-e MYSQL_PASSWORD=wp_password
-p 3306:3306
mysql:5.7

docker run -d --name mywp --link mysql_container:custom_mysql_image -p 80:80 custom_wp(when you dont give any extra parameters and use paramenters as in dcokerfile)
For custom parameters
docker run -d
--name wordpress-container
--link mysql-container:mysql
-v wordpress_data:/var/www/html
-e WORDPRESS_DB_HOST=mysql-container:3306
-e WORDPRESS_DB_USER=wp_user
-e WORDPRESS_DB_PASSWORD=wp_password
-e WORDPRESS_DB_NAME=wp_db
-p 8080:80
custom-wordpress
