#Use official node runtime as the base image
FROM node:22-alpine AS build

#Create a working directory inside the container
WORKDIR /app

#Copy and install dependencies
COPY package.json package-lock.json /app/
RUN npm install

#Copy the rest of the application
COPY . .

#Use distroless image for the final stage
FROM gcr.io/distroless/base

#Copy the image from the initial stage
COPY --from=build . .

#Expose port
EXPOSE 3001

#Run the application
CMD [ "npm", "start" ]