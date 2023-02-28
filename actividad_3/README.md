# Actividad 3

El problema era que en el contenedor del FrontEnd unicamente se instalo Nginx
No se proporciono ningun tipo de configuracion para la aplicacion

Agregando un archivo de configuracion nginx.conf al contenedor, deberia de solucionar el problema. 
El contenido del archivo seria 
```
server {
    listen       80;
    server_name  localhost;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
        try_files $uri /index.html;                 
    }

    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }
}
```

Posteriormente se tiene que indicar en el Dockerfile la copia del archivo al sistema de archivos del contenedor

```
## BUILD
# docker build -t mifrontend:0.1.0-nginx-alpine -f nginx.Dockerfile .
## RUN
# docker run -d -p 3000:80 mifrontend:0.1.0-nginx-alpine
FROM node:18.14.0-buster-slim as compilacion

LABEL developer="jesus guzman" \
      email="susguzman@gmail.com"

ENV REACT_APP_BACKEND_BASE_URL=http://localhost:3800

# Copy app
COPY . /opt/app

WORKDIR /opt/app

# Npm install
RUN npm install

RUN npm run build

# Fase 2
FROM nginx:1.22.1-alpine as runner
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=compilacion /opt/app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

```

