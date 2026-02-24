#STAGE1
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

#STAGE2
FROM node:18-alpine AS runner
WORKDIR /app
COPY --from=builder /app/out ./out
RUN npm install -g serve
EXPOSE 3000
CMD ["serve", "out"]
