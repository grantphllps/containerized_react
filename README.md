#Develop a React app in a container

##Dockerfile

Add a `Dockerfile` to the root of the react app that looks like this:

```
# Use an official Node.js runtime as the base image
FROM node:14

# Set the working directory inside the container
WORKDIR /usr/src/app

# Install dependencies
COPY package*.json ./
RUN npm install

# Expose the port your React app will run on (usually 3000)
EXPOSE 3000

# Start the development server
CMD ["npm", "start"]
```
