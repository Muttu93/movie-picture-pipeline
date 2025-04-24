FROM  public.ecr.aws/docker/library/node:18.14.2-alpine3.17

ARG REACT_APP_MOVIE_API_URL
ENV REACT_APP_MOVIE_API_URL=${REACT_APP_MOVIE_API_URL}
ENV NODE_OPTIONS=--openssl-legacy-provider

WORKDIR /app

# Copy dependdency files
COPY package*.json ./

# Install packages
RUN npm ci

# Copy code
COPY . .

# Build the app
RUN npm run build

RUN npm install -g serve

# Expose the port used by the React app
EXPOSE 3000

# Start the React app when the container starts
CMD [ "serve", "-s", "build"]