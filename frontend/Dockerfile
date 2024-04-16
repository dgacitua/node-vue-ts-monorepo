# https://www.azilen.com/blog/should-you-containerize-your-front-end-apps/

# Build stage
FROM node:20-alpine AS build

WORKDIR /app

COPY package*.json .

RUN npm ci --silent

COPY . .

RUN npm run build

# Production stage
FROM nginx:stable-alpine AS production

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD [ "nginx", "-g", "daemon off;" ]