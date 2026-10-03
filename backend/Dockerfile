FROM node:20-alpine
# openssl: Prisma; python3/make/g++: bcrypt native build when GitHub prebuilds fail (504 / musl)
# git: clone Fybud/CEP platform-api for tenant Prisma client + migrate scripts
RUN apk add --no-cache openssl python3 make g++ git

WORKDIR /app

# Tenant platform-api (lives in Fybud/CEP; needed for org DB features + migrations)
ARG CEP_REPO=https://github.com/Fybud/CEP.git
ARG CEP_REF=main
RUN git clone --depth 1 --branch "$CEP_REF" "$CEP_REPO" /tmp/cep \
  && mv /tmp/cep/platform-api /app/platform-api \
  && rm -rf /tmp/cep

WORKDIR /app/platform-api
RUN npm install --fetch-retries=5 --fetch-retry-mintimeout=20000 --fetch-retry-maxtimeout=120000 \
  && npx prisma generate

# Admin API
WORKDIR /app/backend
COPY package*.json ./
RUN npm install --fetch-retries=5 --fetch-retry-mintimeout=20000 --fetch-retry-maxtimeout=120000
COPY prisma ./prisma
RUN npx prisma generate
COPY . ./

EXPOSE 4200
CMD ["sh", "-c", "npm run db:deploy && npx tsx src/server.ts"]
