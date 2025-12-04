# ---------- Stage 1: Build Frontend ----------
FROM node:20-alpine AS build

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install --legacy-peer-deps

# Copy all source files
COPY . .

# Build the application
RUN npm run build

# ---------- Stage 2: Serve Frontend with Node ----------
FROM node:20-alpine

WORKDIR /app

# Copy built files from build stage
COPY --from=build /app ./

# Install serve package to serve the static files (if using React/Vite)
RUN npm install -g serve

# Expose frontend port
EXPOSE 3000

# Start frontend using serve
CMD ["serve", "-s", "dist", "-l", "3000"]
