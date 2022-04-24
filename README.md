<a><img src="https://i.ibb.co/S51KCkq/Letter-a-logo-icon-design-vector-22731542-removebg-preview-1.png" alt="Stock-vector-bolt-blue-gradient-vector-icon-removebg-preview" border="0"></a>
# Alphactyl-v1
<a><div class="flip-box">
  <div class="flip-box-inner">
    <div class="flip-box-front">
      <img src="https://i.ibb.co/njVRgJW/letter-a-logo-icon-design-vector-22731542-removebg-preview-1.png" alt="Paris" style="width:300px;height:200px">      <img src="https://i.ibb.co/g6szkq7/Screenshot-3.png" alt=" image loding " style="width:300px;height:200px">      <img src="https://i.ibb.co/zxj84L1/Screenshot-4.png" alt="Paris" style="width:300px;height:200px">
    </div>
  </div>
</div>
   </a>
    
# ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) Alphactyl-v1 Will be release soon

[![](https://img.shields.io/badge/github-blue?style=for-the-badge)](https://cp.alphanodes.xyz)
[![](https://img.shields.io/badge/website-blueviolet?style=for-the-badge)](https://cp.alphanodes.xyz)
[![](https://img.shields.io/badge/API-yellow?style=for-the-badge)](https://cp.alphanodes.xyz)
[![](https://img.shields.io/badge/Donate-orange?style=for-the-badge)](https://cp.alphanodes.xyz)

# ![#56666](https://via.placeholder.com/15/Z999999/000000?text=+)Features 

🟢 Client area for pterodactyl game panel 

🟢 Easy to install 

🟢 Discord OAuth2 as a login system.

🟢 Allows users to split resources throughout multiple servers
<bold>Supported panel operating systems and webservers</bold>
<table border="1" color="red">
   <tr>
      <th>Operating System</th>
      <th>Version</th>
       <th>nginx support</th>
   </tr>
   <tr>
      <td>Ubuntu</td>
      <td>14.04</td>
      <td>🔴</td>
   </tr>
    <tr>
      <td></td>
      <td>16.04</td>
      <td>🔴</td>
   </tr>
       <tr>
      <td></td>
      <td>18.04</td>
      <td>🔴</td>
   </tr>
    <tr>
      <td></td>
      <td>20.04</td>
      <td>✅</td>
   </tr>
       <tr>
      <td>Debian</td>
      <td>8</td>
      <td>🔴</td>
   </tr>
       <tr>
      <td></td>
      <td>9</td>
      <td>🔴</td>
   </tr>
       <tr>
      <td></td>
      <td>10</td>
      <td>✅</td>
   </tr>
       <tr>
      <td></td>
      <td>11</td>
      <td>✅</td>
   </tr>
       <tr>
      <td>CentOS</td>
      <td>6</td>
      <td>🔴</td>
   </tr>
       <tr>
      <td></td>
      <td>8</td>
      <td>✅</td>
   </tr>
       <tr>
      <td></td>
      <td>9</td>
      <td>✅</td>
   </tr>
   </table>
    
# ![#f03c15](https://via.placeholder.com/15/S9999/000000?text=+)How to install

# Step 1 Installing Dependencies
   
    & sudo apt install git
   
    & curl -fsSL https://deb.nodesource.com/setup_12.x | sudo bash -
    & apt install nodejs
    & npm -v
    & apt install nginx
    & sudo apt install certbot
    & sudo apt install -y python3-certbot-nginx
   
# Step 2 Downloading Dash files from github
     & cd ../
     & cd /var/www
     & git clone https://
     & cd Alphactyl-v1.0
   
# Step 3 setting up settings.json
       & nano settings.json
 #edit the settings.json file and fill oauth and panel columns correctly then save it by ctrl+x
 
# Step 4 ssl creation for domin
       & systemctl start nginx
       & certbot certonly --nginx -d dash.your-domain
* if cert ssl creation is successful this msg will show
IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/your.dashactyl.domain/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/your.alphactyl.domain/privkey.pem
   Your cert will expire on date. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot
   again. To non-interactively renew *all* of your certificates, run
   "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le
   
       & cd /etc/nginx/sites_enabled
       & touch alphactyl
       &  nano alphactyl.conf
* then paste the script below (change all <domin> to your domin and <port> to the port you want to listen 
dashactyl is hosted.

```Nginx
server {
    listen 80;
    server_name <domain>;
    return 301 https://$server_name$request_uri;
}
server {
    listen 443 ssl http2;
location /afkwspath {
  proxy_http_version 1.1;
  proxy_set_header Upgrade $http_upgrade;
  proxy_set_header Connection "upgrade";
  proxy_pass "http://localhost:<port>/afkwspath";
}
    
    server_name <domain>;
ssl_certificate /etc/letsencrypt/live/<domain>/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/<domain>/privkey.pem;
    ssl_session_cache shared:SSL:10m;
    ssl_protocols SSLv3 TLSv1 TLSv1.1 TLSv1.2;
    ssl_ciphers  HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers on;
    access_log /var/log/nginx/access.log;
location / {
      proxy_pass http://localhost:<port>/;
      proxy_buffering off;
      proxy_set_header X-Real-IP $remote_addr;
  }
}
```

   
Remember to change <domain> to your alphactyl domain.and <port> do the port that dashactyl is hosted
# Step 5 dash  
   
    & systemctl restart nginx
    & cd dashactyl
    & node index.js
* Your output should send the following messgae (Your port will be different
* [WEBSITE] The dashboard successfully loaded on port 80.
* you need to exit the process by clicking ctrl+c

# Step 5 dash
   
    & npm install pm2 -g
    & pm2 start index.js
   
# ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) Disclaimer
This project uder development We are not responsible for any damages.
