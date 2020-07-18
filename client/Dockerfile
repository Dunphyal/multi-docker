FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
#expose the specified port
EXPOSE 3000
# copy form current directory to /etc/.....
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# copy build from the builder phase of the dockerfile
COPY --from=builder /app/build /usr/share/nginx/html