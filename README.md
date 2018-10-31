# Projeto Configuração de Servidor Linux

## O endereço de IP e a porta SSH.
O IP da instância Lightsail criada é 18.215.249.3, mas considerando que o acesso pelo Google Sign In não pode ser feito diretamente somente por IPs, fiz uso do serviço http://xip.io, que geral wildcards DNS para qualquer IP. Portanto o site deve ser acessado pelo endereço:

    http://18.215.249.3.xip.io/

## Softwares e configurações.
- [Ubuntu Linux Server](https://www.ubuntu.com/)

    - Foram negados, através do Firewall do Ubuntu,  acessos para todas as portas, exceto http 80, ssh 2200 e 123/udp
    - Foram criados os usuários catalog e grader e estes foram adicionados como sudoers.
    - Foi configurada a local timezone to UTC para São Paulo.
- [HTTP Server Apache2](https://httpd.apache.org/)
    - Configurei um virtual host no Apache2 utilizando o /etc/apache2/sites-available/catalog.conf para informar o diretório do applicativo.
    - Desabilitei a página padrão do Apache2
- [mod_wsgi](https://pypi.org/project/mod_wsgi/)
    - Criei um módulo catalog.wsgi que importa meu applicativo.
- [PostgreSQL](https://www.postgresql.org/)
    - Foi certificado que o PostgreSQL não recebe acessos remotos.
    - Foi criado um database chamado catalog e configurado o acesso a ele pelo usuário catalog
- [GitHub](https://github.com/)

- [Python 2.7.12](https://www.python.org/)
com os seguintes componentes:
    - sqlalchemy
    - flask
    - httplib2
    - requests
    - oauth2client
    - psycopg2
    - libpq-dev

## Recursos de terceiros
- [Amazon Lightsail](https://aws.amazon.com/)

- http://xip.io

- [Google APIs](https://console.developers.google.com/)

## Chave SSH privada
O usuário grader pode realizar acesso por ssh pela por 2200 (a porta SSH 22 padrão foi fechada e a solicitação de password desabilitada), informando a seguinte chave privada:

[grader_key.pem](grader_key)