#Informa o Container base para baixar do Docker Hub
FROM ubuntu:20.04

#Setando variavel
ENV timezone=America/Sao_Paulo

#Comandos para rodar no ubuntu
RUN apt-get update && \
    ln -snf /usr/share/zoneinfo/${timezone} /etc/localtime && echo ${timezone} > /etc/timezone && \
    apt-get install -y apache2 && \    
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:ondrej/php && \
    apt-get update && \
    apt-get install -y php8.1 && \    
    apt-get install -y php8.1-mysql && \
    apt-get install -y php-xdebug

#Comandos para habilitar modulo htacess do apache2 e configurar apache2.conf
RUN a2enmod rewrite && \
    echo '\n<Directory "/var/www/html">\n'\
    '    Options Indexes FollowSymLinks\n'\
    '    AllowOverride All\n'\
    '    Require all granted\n'\
    '    Options -Indexes\n'\
    '</Directory>' >> /etc/apache2/apache2.conf && \
    #Configurando VirtualHost no apache em sites-available
    echo '\n<VirtualHost *:80>\n'\
    '   ServerName php81.com.br\n'\
    '   ServerAlias www.php81.com.br\n'\
    '   DocumentRoot /var/www/html/php81\n'\
    '</VirtualHost>' >> /etc/apache2/sites-available/php81.com.br.conf && \
    #Habilitar o virtualhost
    a2ensite php81.com.br.conf && \
    #Desabilita o site padrão do apache
    a2dissite 000-default.conf
    
#Porta de Comunicacao
EXPOSE 80

#Diretorio de Trabalho
WORKDIR /var/www/html

#Comando para serem rodados ao final do build
ENTRYPOINT /etc/init.d/apache2 start && /bin/bash