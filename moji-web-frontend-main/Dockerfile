# Build stage
FROM node:18-alpine as build

WORKDIR /app

# Copy package files
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY . .

# Build the app (only for production)
RUN npm run build

# Production stage
FROM nginx:alpine as production

# Copy built files from build stage
COPY --from=build /app/build /usr/share/nginx/html

# Copy nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 3000
EXPOSE 3000

# Start nginx
CMD ["nginx", "-g", "daemon off;"]

# Development stage
FROM build as development

# Expose development port
EXPOSE 3000

# Start development server (this will be the default for development)
CMD ["npm", "start"] 