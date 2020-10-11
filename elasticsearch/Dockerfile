FROM docker.elastic.co/elasticsearch/elasticsearch:7.9.2

COPY ./config/elasticsearch.yml /usr/share/elasticsearch/config/elasticsearch.yml

# remove plugin
# RUN elasticsearch-plugin remove analysis-icu
# RUN elasticsearch-plugin remove analysis-kuromoji

# install plugin
RUN elasticsearch-plugin install analysis-icu
RUN elasticsearch-plugin install analysis-kuromoji
