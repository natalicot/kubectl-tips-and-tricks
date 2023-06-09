# Stage 1: Build
FROM node:14 as build

WORKDIR /app
COPY app.js .

# Stage 2: Run
FROM gcr.io/distroless/nodejs:14
COPY --from=build /app/app.js /app.js
CMD ["app.js"]
