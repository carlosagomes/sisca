# lojong-backend

# Olá seja bem vindo a Documentação da Lojong API.

## Instalação e funcionamento

Para melhor funcionamento dessa aplicação recomenda-se a utilização de *DOCKER* já configurado com todos os pacotes necessários, conforme descrito no seguinte projeto [LOJONG-DOCKER-DEV]( https://github.com/lojongapp/lojong-docker-dev).
 
 Pode ser instalado manualmente com os seguintes pré requisitos. 
 
* PHP 7.3
* MYSQL 5.7
* REDIS
* Instalação vendor packages: `$ composer install`
* Executar local web-server: `$ php artisan serve`
* Executar migrate web-server: `$ php artisan migrate --seed`
* Acessar local instance: http://localhost:8000


## Swagger Documentation

To generate a new swagger json file (or add to deploy routine/github actions), execute the following command:
```
composer run-script create-swagger
```
The generated json is integrated with swagger-ui (in /docs directory) hosted at http://api.devlojong.com



----------

## Itens a baixo estão depreciados 

## Deployment

Deployment is orgaznied using [Deployer](https://deployer.org/).

Deployment is achieved using following command:
```
vendor/bin/dep deploy development
```

List of all commands isd available via `vendor/bin/dep list` command.

Deploy scripts are not tested on Windows operating system. They should be run on Linux or iOS.

## Error monitoring

[Rollbar](https://rollbar.com/lojong/lojong-backend/) is used to track errors.

## Gympass Subscription

To generate an access url and simulate a subscription of a Gympass user, we can use:
```
php artisan gympass:generate {name} {email} {gympass_id}
```

The gympass ID needs to be on the right format for the sendEvents job to work:
```
# gpw-uuid
gpw-455e5a31-5fa6-49d9-8858-07257e5615ae
```

Every hour there is a job running to send events to Gympass servers. For test purposes, we can call the job manually:
```
php artisan gympass:sendEvents
```
