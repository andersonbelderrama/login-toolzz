# Login Toolzz

Desenvolvido por Anderson Belderrama - andersonbelderrama@gmail.com

## Tecnologias Utilizadas

- Vuejs 3 with Javascript
- TailwindCSS for Style
- Laravel for API
- MySQL for Database

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

Popula banco de dados com dados para teste

```sh
php artisan db:seed
```
