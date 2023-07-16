# Stage 1: Build an Angular Docker Image
FROM node as build

WORKDIR /app
COPY angularSample/package*.json /app/
RUN npm install
COPY angularSample /app
ARG configuration=production
RUN npm run build -- --configuration $configuration

# Stage 2, use the compiled app, ready for production with Nginx
FROM nginx

COPY --from=build /app/dist/* /usr/share/nginx/html
COPY nginx-custom.conf /etc/nginx/conf.d/default.conf