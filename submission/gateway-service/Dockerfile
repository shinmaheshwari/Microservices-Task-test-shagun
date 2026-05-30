FROM node:18-alpine

WORKDIR /app

# Install CA certificates (better fix for SSL issues)
RUN apk add --no-cache ca-certificates

# Copy dependency files first (for caching)
COPY package*.json ./

# Disable strict SSL + install dependencies
RUN npm config set strict-ssl false \
    && npm install --omit=dev

# Copy application code
COPY . .

# Expose port (change per service)
EXPOSE 3003

# Start application
CMD ["node", "app.js"]
