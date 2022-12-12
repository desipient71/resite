
```
### vps_deployment
```
1. create ssl website(using certbot and nginx), and configure nginx as follow:
   vi /etc/nginx/sites-enabled/default:
   ...
   server {
      server_name site.your.domain.name
      location / {
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_pass       http://127.0.0.1:8011;
      }
   }
2. systecmctl start nginx
3. npm install -g forever
4. git clone https://github.com/desipient71/resite.git; 
5. cd resite; npm install;
6. replace serverName in 'config.js', like:
   serverName: 'site.herokuapp.com' ====> 'site.your.domain.name'
7. forever start -c 'node --tls-min-v1.0' index.js
8. done, now you can access your domain name from browser.
```

