# The devops part of the paper project

## How to use:

### 1. Clone and pull this repo in the same directory where the NodeJS microservices are

### 2. run in the console "docker-compose up --build"

### 3. (Only if runs for an initial time ot that machine)

bash> chmod +x ./init-letsencrypt.sh
bash> ./init-letsencrypt.sh

This procedure will register the certbot and insert a keys for the SSL encription

# To renew the SSL certificates for the blurpaper.com and www.blurpaper.com site then use:
## Approach 1: (Unfortunetly this approach temporary doesn't work. Use the below one)
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

## Approach 2: (Just run "bash init-letsencrypt.sh"):
Then add the according TXT records in the domain dns.
This method is easier but not very easy automatable.

# To renew the SSL certificate for the cdn.blurpaper.com subdomain then use:
## Approach 1: (Currently not working):
- bash init-letsencrypt-cdn.sh
- Thant should be all. If not comment / uncomment the according sections in the 000-default.conf

## Approach 2: (The same as above Approach 2 but run "bash cdn-letsencrypt.sh" instead)

# To add more options for the mailserver:
- Update: paper-devops/data/dms/config/postfix-master.cf
- See how the syntax is written
- Search for the property that should be added
- See this link for more info: https://docker-mailserver.github.io/docker-mailserver/latest/config/advanced/override-defaults/postfix/
- Search for the service and type for the property: https://www.postfix.org/qmgr.8.html
- After add the proeprty:
  - docker-compose down (to stop fully the mailserver)
  - docker-compose up ... --build mailserver
  - See is there an errors while trying to configure the server
  - If there are some errors most probably the property is not added with the appropriate service/type
