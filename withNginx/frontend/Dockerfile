# Stage 1: Build the Next.js application
FROM node:18-alpine AS builder

WORKDIR /app

COPY package.json yarn.lock ./
RUN yarn install

COPY . .

RUN yarn build

# Stage 2: Serve the Next.js application with Nginx
FROM nginx:stable-alpine AS runner

COPY --from=builder /app/out /usr/share/nginx/html

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]