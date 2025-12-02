# ---------- Stage 1: Build Frontend ----------
FROM node:20-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install --legacy-peer-deps

COPY . .
RUN npm run build


# ---------- Stage 2: Serve Using NGINX ----------
FROM nginx:alpine

# Copy build output to Nginx html
COPY --from=build /app/dist /usr/share/nginx/html
# OR for React: /app/build

# Replace default nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
