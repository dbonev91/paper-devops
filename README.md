# The devops part of the paper project

## How to use:

### 1. Clone and pull this repo in the same directory where the NodeJS microservices are

### 2. run in the console "docker-compose up --build"

### 3. (Only if runs for an initial time ot that machine)

bash> chmod +x ./init-letsencrypt.sh
bash> ./init-letsencrypt.sh

This procedure will register the certbot and insert a keys for the SSL encription

# To renew the SSL certificates for the blurpaper.com and www.blurpaper.com site then use:
1. Go to 000-default.conf in apache server
2. uncomment the 5025 section
3. comment the below sections (blurpaper.com and www.blurpaper.com)
4. in the ssh console:
  - service apache2 stop
  - service apache2 start
  - service apache2 restart
  - bash init-letsencrypt.sh
  - rebuld the docker services
  - in the 000-default.conf comment as the records was in the beggining

# To renew the SSL certificate for the cdn.blurpaper.com subdomain then use:
- bash init-letsencrypt-cdn.sh
- Thant should be all. If not comment / uncomment the according sections in the 000-default.conf
