# base docker NODE image
FROM node:15.6.0-alpine3.12 as builder

# set working directory in the container
WORKDIR /app

# copy just package.json to avoid executing npm install when there is no changes in package.json
COPY ./package.json ./

#install dependecies
RUN npm install --force

# copy the project
COPY . .

# build the application
RUN npm run build

FROM nginx:1.18-alpine
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/dist/employees-ui /usr/share/nginx/html