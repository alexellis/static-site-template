FROM openfaas/of-watchdog:0.5.3 as watchdog

FROM nginxinc/nginx-unprivileged:mainline
USER root
COPY --from=watchdog /fwatchdog /usr/bin/fwatchdog
RUN chmod +x /usr/bin/fwatchdog

WORKDIR /usr/share/nginx/html
COPY function .

RUN sed -ie s/8080/8082/g /etc/nginx/conf.d/default.conf
RUN echo -n "daemon off;" | tee -a /etc/nginx/nginx.conf

ENV fprocess="nginx"
ENV mode="http"
ENV upstream_url="http://127.0.0.1:8082"

RUN chown -R nginx:nginx *

USER nginx

CMD ["/usr/bin/fwatchdog"]
