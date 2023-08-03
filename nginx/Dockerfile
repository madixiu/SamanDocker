# production stage
FROM nginx:1.24.0 as production-stage
COPY nginx/nginx.conf /etc/nginx/nginx.conf
# COPY backend/static /usr/src/app/static/
# COPY --from=build-stage /frontend/dist /dist/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]