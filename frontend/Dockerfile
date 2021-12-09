FROM node:12-alpine3.14 as builder
WORKDIR /app
COPY frontend/ /app
RUN npm install
#RUN find /app/src -type f -iname '*Api.js' -print0| xargs -0 sed -i "s/localhost:8000/backend:8000/g"

FROM node:12-alpine3.14
COPY --from=builder /app /app
WORKDIR /app
CMD [ "npm", "start" ]
