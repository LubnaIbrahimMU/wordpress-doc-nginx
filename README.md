and in sudo nano /etc/nginx/sites-available/default

***
/
upstream wordpress  {
    server localhost:8081 weight=1;
    server localhost:8082 weight=1;
}

server {


    listen 80;
    server_name localhost;

    location /  {
        proxy_pass http://wordpress;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}

\
***
