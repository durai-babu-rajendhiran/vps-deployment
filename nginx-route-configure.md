# Node.js configuration
```
server {
    listen 80;
    location / {
        proxy_pass http://your_server_ip:5001/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

# React.js configuration
```
server {
    listen 80;
    server_name your_domain www.your_domain;
    location / {
        root /var/www/your_domain/client;
        index index.html index.htm;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        try_files $uri $uri/ /index.html;
    }
}
```

# Node.js set IP address
```
location /api/ {
    proxy_pass http://your_server_ip:6001/;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
}
```

# .NET configuration
```
server {
    server_name your_domain www.your_domain;
    location / {
        proxy_pass http://localhost:5000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection keep-alive;
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

# Django app configuration
```
server {
    listen 80;
    server_name your_domain;
    location = /favicon.ico { access_log off; log_not_found off; }
    location /static/ {
        root /repos/djangoapp/djangoapi;
    }
    location / {
        include proxy_params;
        proxy_pass http://unix:/run/gunicorn.sock;
    }
}
```

# Next.js configuration
```
server {
    listen 80;
    server_name your_domain www.your_domain;
    location /_next/static/ {
        alias /repos/nextjsapp/.next/static/; # !!! - change to your app name
        expires 365d;
        access_log off;
    }
    location / {
        proxy_pass http://127.0.0.1:3000; # !!! - change to your app port
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```
