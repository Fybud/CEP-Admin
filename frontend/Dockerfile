FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM node:20-bookworm-slim
WORKDIR /app
ENV NODE_ENV=production
COPY --from=builder /app/dist ./dist
COPY docker-entrypoint.sh /docker-entrypoint.sh
RUN npm install -g serve \
  && chmod +x /docker-entrypoint.sh \
  && printf '%s\n' 'window.__ENV__ = window.__ENV__ || {};' > /app/dist/env.js
EXPOSE 5173
ENTRYPOINT ["/docker-entrypoint.sh"]
