FROM node:20-bullseye

WORKDIR /app

COPY package*.json ./

RUN apt-get update && apt-get install -y \
    python3 make g++ git build-essential \
    && rm -rf /var/lib/apt/lists/*

RUN npm install

COPY . .

EXPOSE 3000
CMD ["npm", "run", "dev"]
