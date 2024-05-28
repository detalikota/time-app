FROM node:19.5.0-alpine
WORKDIR /app
EXPOSE 5000
COPY package*.json ./
RUN npm install
COPY . ./
CMD ["npm", "run", "dev"]