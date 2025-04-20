FROM node:20-alpine AS build
WORKDIR /app
COPY angular-project/package*.json ./
RUN npm install --cache /npm/cache --prefer-offline
COPY angular-project/ ./
RUN npm run build

FROM nginx:alpine
COPY nginx/nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist/angular-project/browser /usr/share/nginx/html
EXPOSE 80
CMD ["nginx","-g","daemon off;"]
