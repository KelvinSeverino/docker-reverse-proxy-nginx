#Informa o Container base para baixar do Docker Hub
FROM nginx:1.21.6

#Criando diretorios para armazenar as configuracoes das aplicacoes
RUN mkdir /etc/nginx/conf.d/sites-available && \
    mkdir /etc/nginx/conf.d/sites-enabled

#Copiando os arquivos de configuracoes para o container
COPY ./sites-available/php74.conf ./sites-available/php81.conf /etc/nginx/conf.d/sites-available/

#Criando um link sombolico no sites-enabled com os arquivos do sites-available
RUN cd /etc/nginx/conf.d/sites-enabled && \
    ln -s /etc/nginx/conf.d/sites-available/php74.conf && \
    ln -s /etc/nginx/conf.d/sites-available/php81.conf

#Copiando os arquivos de configuracoes para o container
COPY ./nginx.conf /etc/nginx/

#Porta de Comunicacao
EXPOSE 80

#Diretorio de Trabalho
WORKDIR /etc/nginx

#Comando para serem rodados ao final do build
ENTRYPOINT /etc/init.d/nginx start && /bin/bash