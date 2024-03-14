# Login Toolzz

Desenvolvido por Anderson Belderrama - andersonbelderrama@gmail.com

## Tecnologias Utilizadas

- Vuejs 3 with Javascript
- TailwindCSS for Style
- Laravel for API
- MySQL for Database
- Docker for Development

## Estrutura do Projeto

Projeto está dividido em 2 projetos distintos frontend e backend, tendo a possibilidade de ter melhor manutenção e deploy em ambientes indepentendes.
Essa é algumas de muitos outros beneficios de trabalhar com front e back separados.

## Comandos Frontend

Caminho para executar qualquer comando destinado ao frontend

```sh
cd frontend
```

Instalar as dependencias do projeto(node_modules)

```sh
npm install
```

Copile e ative hot-reload para ambiente de desenvolvimento

```sh
npm run dev
```

Copile e minifique para ambiente de produção

```sh
npm run build
```

## Comandos Backend

Caminho para executar qualquer comando destinado ao frontend

```sh
cd backend
```

Copie .env.example e configure o banco de dados

```sh
cp .env.example .env
```

Comando para funcionamento do laravel

```sh
composer install
```
```sh
php artisan key:generate
```

Gerar tabelas no banco de dados configurado

```sh
php artisan migrate
```

Popula banco de dados com dados fake para teste

```sh
php artisan db:seed
```

Executa servidor de desenvolvimento PHP

```sh
php artisan serve
```

## Docker Backend (Avançado)

Precisa ter instalado docker e docker-compose no seu ambiente para seguir os passos abaixo.

Iniciar serviços(web, banco de dados)

```sh
./vendor/bin/sail up -d
```

Parar serviços(web, banco de dados)

```sh
./vendor/bin/sail down
```

## Informação Adicional

- User/Password: test@test.com/password
- Url Frontend: localhost:5173
- Endpoints Frontend: / & /login
- Url Backend: localhost/api
- Endpoints Backend /login & /logout & /user