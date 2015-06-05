# docker-atlas

Stellar's container for storing/viewing metrics using [Netflix's
Atlas](https://github.com/Netflix/atlas) time series store.

Note that this image automatically accepts the oracle-java8-installer license
so by using this image you indicate that you agree to that license. At least I
suspect so. I am not a lawyer.

## Usage

The recommended way to run this container looks like this:

```console
$ docker run --name atlas -p 7101:7101 -d stellar/atlas
```

Atlas will then be available at port 7101 of your docker host. You can confirm via something like

```console
$ curl http://boot2docker:7101/api/v1/tags
```
