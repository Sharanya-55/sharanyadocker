# Stage 1: Build Angular App
FROM node:16 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build -- --configuration production


# Stage 2: Serve with nginx
FROM nginx:alpine
COPY --from=build /app/dist/my-angular-app/my-angular-app /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

