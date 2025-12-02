FROM node:20-alpine

WORKDIR /app

# Install only production deps
COPY package*.json ./
RUN npm install --production --legacy-peer-deps

COPY . .

EXPOSE 5000

CMD ["npm", "start"]
