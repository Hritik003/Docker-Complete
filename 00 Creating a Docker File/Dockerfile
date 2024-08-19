FROM  node

WORKDIR /app

COPY package.json /app

RUN npm install 

COPY . /app
# ./ relative path now points to app directory, since the working dir is "app"

EXPOSE 80

CMD ["node", "server.js"]



