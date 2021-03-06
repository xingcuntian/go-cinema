# Cinema - Example of Microservices in Go with Docker and MongoDB

Requirements
===========

* Docker 1.12
* Docker Compose 1.8

We must **add virtual domains** in order to use each **api entry point**. By default we are using: **movies.local**, **bookings.local**, **users.local** and **showtimes.local**

**Virtual domains** has been defined in `docker-compose.yml` file and configured in `/etc/hosts` file. Add the following line in your `/etc/hosts` file:

```
127.0.0.1   movies.local bookings.local users.local showtimes.local
```

Starting services
==============================

```
docker-compose up -d
```

Stoping services
==============================

```
docker-compose stop
```

Including new changes
==============================

```
docker-compose build
```

Restore database information
======================
**_Access to mongodb container typing:_**

```
docker exec -it cinema-db /bin/bash
```

**_Restore data typing:_**

```
/backup/restore.sh
```

**_Leave the container:_**

```
exit
```


Documentation
======================

## User Service

This service returns information about the users of Cinema.

**_Routes:_**

* GET - http://users.local/users : Get all users
* POST - http://users.local/users : Create user
* DELETE - http://users.local/users/{id} : Remove user by id

## Movie Service

This service is used to get information about a movie. It provides the movie title, rating on a 1-10 scale, director and other information.

**_Routes:_**

* GET - http://movies.local/movies : Get all movies
* POST - http://movies.local/movies : Create movie
* GET - http://movies.local/movies/{id} : Get movie by id
* DELETE - http://movies.local/movies/{id} : Remove movie by id

## Showtimes Service

This service is used get a list of movies playing on a certain date.

**_Routes:_**

* GET - http://showtimes.local/showtimes : Get all showtimes
* POST - http://showtimes.local/showtimes : Create showtime
* GET - http://showtimes.local/showtimes/{id} : Get showtime by id
* DELETE - http://showtimes.local/showtimes/{id} : Remove showtime by id

## Booking Service

Used to lookup booking information for users.

**_Routes:_**

* GET - http://bookings.local/bookings : Get all bookings
* POST - http://bookings.local/bookings : Create booking

### Significant Revisions

* [Microservices - Martin Fowler](http://martinfowler.com/articles/microservices.html)
* [Web Development with Go](http://www.apress.com/9781484210536)
* [Umer Mansoor - Cinema](https://github.com/umermansoor/microservices)