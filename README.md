# Docker Reverse Proxy NGINX

## Requisitos

- WSL2 (Opcional)
- Docker
- Docker-compose

## Docker
Com o ambiente linux tendo instalado o docker e docker-compose vamos rodar os comandos de forma linear abaixo:

Clonar o repositorio
```sh
git clone https://github.com/KelvinSeverino/docker-reverse-proxy-nginx.git
```

Acessar o diretório raiz do projeto e executar o docker-compose
```sh
docker-compose up -d
```

Criar um arquivo para simular DNS local, para este cenário usarei no Windows pelo arquivo hosts que fica em **C:\Windows\System32\drivers\etc\hosts**

```bash
127.0.0.1	php74.com.br
::1	php74.com.br

127.0.0.1	php81.com.br
::1	php81.com.br
```

Com os passsos acima realizados com sucesso, os containers estarão online e para validar o funcionamento das multiplas versões do PHP com acesso direto pela porta 80 cedidade pelo Proxy Reverso do NGINX, acesse no navegador http://php74.com.br para o PHP 7.4 e http://php81.com.br para o PHP 8.1