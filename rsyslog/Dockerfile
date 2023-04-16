FROM ubuntu:latest

RUN apt-get update && apt-get install -y rsyslog &&  mkdir -p /var/log/log_server/

RUN apt-get install nano
 
COPY ./conf.d/rsyslog.conf /etc/rsyslog.conf

#RUN chown syslog:adm /var/log/log_server/

EXPOSE 514/tcp 514/udp


CMD ["rsyslogd", "-n"]
