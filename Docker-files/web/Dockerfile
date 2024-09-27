FROM nginx:latest
LABEL "Project"="VProfile"
LABEL "Author"="IngCloud"
RUN rm -rf /etc/nginx/conf.d/default.conf
COPY nginvproapp.conf /etc/nginx/conf.d/default.conf