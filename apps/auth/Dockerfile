# Development build stage
FROM node:alpine AS development

WORKDIR /usr/src/app

COPY package.json .
COPY package-lock.json .
RUN npm install

COPY . .
RUN npm run build

# Production build stage
FROM node:alpine AS production

WORKDIR /usr/src/app

COPY package.json .
COPY package-lock.json .
RUN npm install --prod

COPY --from=development /usr/src/app/dist ./dist

CMD ["node", "/usr/src/app/dist/apps/auth/main.js"]
