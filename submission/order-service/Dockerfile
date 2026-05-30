FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy only package files first (cache optimization)
COPY package*.json ./

# Install only production dependencies
RUN npm ci --only=production

# Copy application code
COPY . .

# Expose correct port
EXPOSE 3000

# Start application
CMD ["node", "app.js"]
