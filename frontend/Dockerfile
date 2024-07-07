# # Dockerfile for React Frontend

# FROM node:14

# # Set the working directory
# WORKDIR /app

# # Copy package.json and package-lock.json
# COPY package.json package-lock.json /app/

# # Install dependencies
# RUN npm install

# # Copy the rest of the application
# COPY . /app

# # Expose the development server port
# EXPOSE 3000

# # Run the development server
# CMD ["npm", "run", "dev"]


# Dockerfile for React

FROM node:14

WORKDIR /app

COPY package*.json /app

RUN npm install

COPY . /app

RUN npm run build

EXPOSE 3000

CMD ["npm", "start"]
