# Set the base image for the frontend
FROM node:20 AS builder

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the application
RUN npm run build

# Set the base image for serving the app
FROM node:20

# Set the working directory
WORKDIR /app

# Copy built files from the builder stage
COPY --from=builder /app/.next /app/.next
COPY --from=builder /app/package*.json /app/
COPY --from=builder /app/public /app/public

# Install only production dependencies
RUN npm install --only=production

# Expose the port the app runs on
EXPOSE 3000

# Start the application
CMD ["npm", "start"]
