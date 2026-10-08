FROM node:26-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --omit=dev
FROM node:26-alpine
WORKDIR /app
RUN addgroup -S mackllc && adduser -S mackllc -G mackllc
COPY --from=builder /app/node_modules ./node_modules
COPY src ./src
COPY package.json .
USER mackllc
EXPOSE 3000
CMD ["node", "src/index.js"]