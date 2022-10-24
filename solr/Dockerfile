FROM solr:7.5.0
WORKDIR /opt/solr/server/solr
RUN mkdir test \
 && cp /opt/solr/dist/solr-dataimporthandler-7.5.0.jar /opt/solr/server/solr-webapp/webapp/WEB-INF/lib \ 
 && cp /opt/solr/dist/solr-dataimporthandler-extras-7.5.0.jar /opt/solr/server/solr-webapp/webapp/WEB-INF/lib
COPY mysql-connector-java-8.0.14.jar /opt/solr/server/solr-webapp/webapp/WEB-INF/lib
WORKDIR /opt/solr/server/solr/test
RUN echo 'name=test' > core.properties
RUN mkdir data
RUN cp -r ../configsets/_default/conf/ .
WORKDIR /opt/solr/server/solr/test/conf
ADD db-data-config.xml .
ADD solrconfig.xml .
ADD managed-schema.xml .
EXPOSE 8983