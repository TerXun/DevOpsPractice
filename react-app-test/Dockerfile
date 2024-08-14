# FROM node:16.14.0-alpine3.14 AS build_image
# RUN apk add --no-cache nodejs npm
# WORKDIR /isuru
# COPY package.json ./
# RUN npm install
# COPY . .
# RUN npm run build

# FROM node:16.14.0-alpine3.14
# WORKDIR /webapp
# COPY --from=build_image /isuru /webapp/
# EXPOSE 3000
# CMD [ "npm", "start" ]

# pull official base image
FROM node:13.12.0-alpine

# set working directory
WORKDIR /app

# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH

# install app dependencies
COPY package.json ./
COPY package-lock.json ./
RUN npm install --silent
RUN npm install react-scripts@3.4.1 -g --silent

# add app
COPY . ./

# start app
CMD ["npm", "start"]