<p align="center"><img src="https://pixelfed.nyc3.cdn.digitaloceanspaces.com/logos/pixelfed-full-color.svg" width="300px"></p>

<p align="center">
<a href="https://circleci.com/gh/pixelfed/pixelfed"><img src="https://circleci.com/gh/pixelfed/pixelfed.svg?style=svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/pixelfed/pixelfed"><img src="https://poser.pugx.org/pixelfed/pixelfed/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/pixelfed/pixelfed"><img src="https://poser.pugx.org/pixelfed/pixelfed/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/pixelfed/pixelfed"><img src="https://poser.pugx.org/pixelfed/pixelfed/license.svg" alt="License"></a>
</p>

## Introduction

A free and ethical photo sharing platform, powered by ActivityPub federation.

<p align="center">
<img src="https://pixelfed.nyc3.cdn.digitaloceanspaces.com/media/Screen%20Shot%202019-09-08%20at%2010.40.54%20PM.png">
</p>

## Official Documentation

Documentation for Pixelfed can be found on the [Pixelfed documentation website](https://docs.pixelfed.org/).

## License

Pixelfed is open-sourced software licensed under the AGPL license.

## Communication

The ways you can communicate on the project are below. Before interacting, please
read through the [Code Of Conduct](CODE_OF_CONDUCT.md).

* IRC: #pixelfed on irc.freenode.net ([#freenode_#pixelfed:matrix.org through
Matrix](https://matrix.to/#/#freenode_#pixelfed:matrix.org))
* Project on Mastodon: [@pixelfed@mastodon.social](https://mastodon.social/@pixelfed)
* E-mail: [hello@pixelfed.org](mailto:hello@pixelfed.org)


## Pixelfed Sponsors

We would like to extend our thanks to the following sponsors for funding Pixelfed development. If you are interested in becoming a sponsor, please visit the Pixelfed [Patreon Page](https://www.patreon.com/dansup/overview)

- [NLnet Foundation](https://nlnet.nl) and [NGI0
Discovery](https://nlnet.nl/discovery/), part of the [Next Generation
Internet](https://ngi.eu) initiative.
- [<img src="https://td-misc-public.s3.amazonaws.com/OscillasLogo.png" width="100px">](https://oscillas.com/)
- Managed Pixelfed Hosting by [Spacebear](https://app.spacebear.ee/)

## Build from Docker compose

```
cd ~/
git clone https://github.com/JustHumanz/pixelfed
cd pixelfed
cp .env.example .env
vim .env
```
Change the domain name if you want  
<img src="https://raw.githubusercontent.com/JustHumanz/pixelfed/dev/img/1.png">  
Setup database username and password  
<img src="https://raw.githubusercontent.com/JustHumanz/pixelfed/dev/img/2.png">  

Then setup docker-compose.yml  
If you have a traefik running, uncomment this to expose Pixelfed  
<img src="https://raw.githubusercontent.com/JustHumanz/pixelfed/dev/img/3.png">  

If you have a standard reverse proxy, uncommit this to expose Pixelfed and change the port with your reverse proxy
<img src="https://raw.githubusercontent.com/JustHumanz/pixelfed/dev/img/4.png">


Now we should be able to start the services and generate an APP_KEY.  
```
docker exec -it pixelfed_app_1 php artisan key:generate
```
And now we can restart, clear the cache and run the migrations on the database.
```
docker exec -it pixelfed_app_1 php artisan config:cache
docker exec -it pixelfed_app_1 php artisan migrate
#yes
```
And done~  
<img src="https://raw.githubusercontent.com/JustHumanz/pixelfed/dev/img/5.png">
