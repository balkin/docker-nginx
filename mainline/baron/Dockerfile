FROM debian:stretch-slim

EXPOSE 80

STOPSIGNAL SIGTERM

CMD ["nginx", "-g", "daemon off;"]

RUN set -x \
	&& apt-get update \
	&& apt-get install --no-install-recommends --no-install-suggests -y sudo curl wget ca-certificates \
	&& curl -o /tmp/ngxpagespeedinstall -f -L -sS https://ngxpagespeed.com/install 

RUN bash /tmp/ngxpagespeedinstall --nginx-version latest -y

# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stderr /var/log/nginx/error.log

