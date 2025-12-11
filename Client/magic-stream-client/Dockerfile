# # Optimised for dev
# FROM node:20-alpine

# WORKDIR /app

# # Install dependencies only when needed
# COPY package*.json ./
# RUN npm ci

# # Copy app source
# COPY . .

# # Expose Vite dev port
# EXPOSE 5173

# # Default command for development
# CMD ["npm", "run", "dev", "--", "--host"]


# Optimised for production
# --- Build stage ---
FROM node:20-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build


# --- Production stage ---
FROM nginx:stable-alpine

# Copy built files from Node to Nginx HTML directory
COPY --from=build /app/dist /usr/share/nginx/html

# Expose Nginx port
EXPOSE 80

# Run Nginx
CMD ["nginx", "-g", "daemon off;"]



# old

# FROM node

# WORKDIR /app

# COPY package*.json ./
# RUN npm install

# COPY . .

# EXPOSE 5173

# CMD ["npm", "run", "dev", "--", "--host"]
