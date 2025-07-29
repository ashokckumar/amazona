# Use the official Node.js image for building the frontend
FROM node:18 AS build

WORKDIR /app
COPY . .

# Install dependencies and build the React app
RUN npm install
RUN npm run build

# Use NGINX to serve the production build
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

# Copy a custom nginx config if needed
# COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

