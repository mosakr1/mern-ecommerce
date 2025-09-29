# Build stage
FROM node:18-alpine as build

WORKDIR /app

# Copy package.json and install deps
COPY frontend/package*.json ./
RUN npm install --legacy-peer-deps

# Copy source code
COPY frontend/ ./

RUN npm run build

# Serve stage with Nginx
FROM nginx:alpine

# Remove default nginx static files
RUN rm -rf /usr/share/nginx/html/*

# Copy build files to nginx
COPY --from=build /app/build /usr/share/nginx/html
COPY frontend/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 2000
CMD ["nginx", "-g", "daemon off;"]