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

Atlas will then be available at port 7101 of your docker host. You can confirm
via something like

```console
$ curl http://boot2docker:7101/api/v1/tags
```

## Resolution

By default this container will use the `atlas.1m.conf` file, but you can
override this by passing an argument to the run script.

For example if you want to run with 1s resolution run:

```console
$ docker run --name atlas -p 7101:7101 \
    -d stellar/atlas \
    /start /etc/atlas/atlas.1s.conf
```

## Overriding config

You can override config entirely by mounting a volume with your own file and
running that configuration like so:

```console
$ docker run --name atlas -p 7101:7101 \
    -v /path/to/my/conf:/etc/atlas \
    -d stellar/atlas \
    /start /etc/atlas/my.atlas.conf
```
