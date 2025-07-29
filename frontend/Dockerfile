FROM node:18 AS build

WORKDIR /app

# Add this line 👇 before installing dependencies
ENV NODE_OPTIONS=--openssl-legacy-provider

COPY . .

RUN npm install
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

