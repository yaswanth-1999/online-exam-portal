# Build stage
FROM node:18-alpine AS build
 
WORKDIR /usr/frontend
 
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
 
# Runtime stage
FROM node:18-alpine
 
WORKDIR /usr/frontend
 
COPY --from=build /usr/frontend/build ./build
RUN npm install -g serve
 
EXPOSE 3000
CMD ["serve", "-s", "build"]
