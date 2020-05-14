FROM openshift/base-centos7
MAINTAINER Santiago Aponte
RUN yum install httpd -y
RUN yum install epel-release -y
RUN yum install python-pip -y
RUN pip install flask
RUN yum install mod_wsgi -y
RUN yum install mysql-devel -y
RUN yum install python-devel -y
RUN pip install flask-mysqldb
RUN pip install Flask-WTF
RUN pip install passlib 
#RUN mkdir /var/www/my-project
COPY httpd.conf/ /etc/httpd/conf/
WORKDIR /var/www/my-project/app/templates/includes
#COPY app/requirements.txt /app
#RUN  pip install mysql-connector
COPY run.py/ /var/www/my-project
COPY config.py/ /var/www/my-project
COPY application.wsgi/ /var/www/my-project
COPY app/ /var/www/my-project/app
COPY app/templates /var/www/my-project/app/templates
COPY app/templates/includes /var/www/my-project/app/templates/includes
#COPY run.py /var/www/my-project
RUN chmod -R 777 /var/www
EXPOSE 80
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
