# Specify Node Version and Image
# Name Image development (can be any thing)
FROM node:14 AS development

# Specity Working directory inside container
WORKDIR /ait/src/app

# Copy package-lock.json & package.json form host to inside container working directory
COPY package*.json ./

#Install deps inside container
RUN npm install

# Bundle app source
COPY . .

RUN npm run build

EXPOSE 3000

# PRODUCTION
# Build another image name production
FROM node:14 AS produciton

ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}

# Set work dir
WORKDIR /ait/src/app

COPY --from=development /ait/src/app .

EXPOSE 3000

#run app

CMD ["node", "dist/main"]

