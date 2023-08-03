# Develop a React app in a container

## Web App

Create a react app. If you already have one then skip to the "Dockerfile" section, or you can use the template in this repo for a blank project. Otherwise you can create an app with `npx create-react-app my-app`

## Dockerfile

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
Build the container with a command like:

```docker build -t my-react-app-dev .```

Once the container is built, run it with a command like:

```docker run -it -p 3000:3000 --rm -v $(pwd):/usr/src/app my-react-app-dev```

Open a browser and go to `localhost:3000` to see the web app running. Edits made in the `src` on the host will be reflected in the web app.
