FROM node:18-alpine

# Create app directory
WORKDIR /usr/src/app

# Copy package files
COPY package*.json ./

# Install dependencies including development dependencies
RUN npm install

# Copy source code
COPY . .

# Expose port 3001
EXPOSE 3001

# Default to production, can be overridden
ENV NODE_ENV=production

# Start command will be overridden by docker-compose in development
CMD ["npm", "start"] 