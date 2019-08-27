# build stage
#FROM golang:1.12.5-alpine3.9 as build-stage
#WORKDIR /app

#COPY main.go ./

#RUN go build main.go

# production stage
FROM nginx:1.17-alpine
LABEL authors="Hongqi Zhang <zhanghongqi@hotmail.com>"
ARG datapath=/usr/share/nginx/html
ARG user=myuser
ARG group=mygroup
ENV port 80
RUN addgroup  ${group} \
  && adduser -G ${group} -s /bin/bash -D ${user}


COPY index.htm  $datapath/index.html
COPY index_files $datapath/index_files
COPY wavecloud.key /etc/ssl
COPY wavecloud.crt /etc/ssl
COPY ssl.conf      /etc/nginx/conf.d
EXPOSE ${port} 443


#USER ${user}

#CMD /main $port
#CMD while true;do echo "wait 2..";sleep 2; done
