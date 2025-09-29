FROM node:18-alpine

WORKDIR /app

# Copy package.json and install deps
COPY backend/package*.json ./
RUN npm install --production

# Copy source code
COPY backend/ ./

EXPOSE 8000

CMD [ "npm", "start" ]