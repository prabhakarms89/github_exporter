# GitHub Exporter

[![Build Status](http://github.dronehippie.de/api/badges/exporters/github/status.svg)](http://github.dronehippie.de/exporters/github)
[![Go Doc](https://godoc.org/github.com/exporters/github?status.svg)](http://godoc.org/github.com/exporters/github)
[![Go Report](http://goreportcard.com/badge/github.com/exporters/github)](http://goreportcard.com/report/github.com/exporters/github)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/7812da994c7541a39d41e9b505c8fe7f)](https://www.codacy.com/app/exporters/github?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=exporters/github&amp;utm_campaign=Badge_Grade)
[![](https://images.microbadger.com/badges/image/exporters/github.svg)](http://microbadger.com/images/exporters/github "Get your own image badge on microbadger.com")
[![Join the Matrix chat at https://matrix.to/#/#prometheus-exporters:matrix.org](https://matrix.to/img/matrix-badge.svg)](https://matrix.to/#/#prometheus-exporters:matrix.org)

[Prometheus](https://prometheus.io/) exporter that collects GitHub metrics.


## Installation

If you are missing something just write us on our nice [Matrix](https://matrix.to/#/#prometheus-exporters:matrix.org) or [IRC](https://webchat.freenode.net/?channels=prometheus-exporters) channel. If you want to use our pre-built binaries just head over to the [releases](https://github.com/exporters/github/releases).


### Docker

```
docker pull exporters/github:0.1
docker run --rm -p 9212:9212 -e DEBUG=true -e GITHUB_ORGS=exporters -e GITHUB_REPOS=prometheus/prometheus,prometheus/alertmanager exporters/github:0.1
```

If you are using docker-compose to orchestrate your Prometheus setup you can use this quite simple snippet:

```
github_exporter:
    image: exporters/github:0.1
    restart: always
    environment:
    - DEBUG=true
    - GITHUB_ORGS=exporters
    - GITHUB_REPOS=prometheus/prometheus,prometheus/alertmanager
    ports:
    - "127.0.0.1:9212:9212"
```


## Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| DEBUG | `false` | If set to true also debug information will be logged, otherwise only info |
| GITHUB_ORGS |  | List of watched organizations |
| GITHUB_REPOS |  | List of watched repositories |
| GITHUB_USERNAME |  | Username for the GitHub authentication |
| GITHUB_PASSWORD |  | Password for the GitHub authentication |
| GITHUB_TOKEN |  | Token for the GitHub authentication |
| WEB_ADDR | `:9212` | Address for this exporter to run |
| WEB_PATH | `/metrics` | Path for metrics  |


## Metrics


| Name | Type | Cardinality | Help |
|------|------|-------------|------|
| github_ | gauge | 1 | Description |


### Alerts & Recording Rules

Example alerts and recording rules you can find at [example.rules](example.rules)


## Development

Make sure you have a working Go environment, for further reference or a guide take a look at the [install instructions](http://golang.org/doc/install.html). It is also possible to just simply execute the `go get github.com/exporters/github` command, but we are mostly using our `Makefile`. Make sure you copy the `.env.example` to `.env` and change the variables matching your credentials.

```
go get -d github.com/exporters/github
cd $GOPATH/src/github.com/exporters/github
make build && ./github_exporter
```


## Contributing

Fork -> Patch -> Push -> Pull Request


## Authors

* [Thomas Boerger](https://github.com/tboerger)


## License

Apache-2.0


## Copyright

```
Copyright (c) 2017 Thomas Boerger <thomas@webhippie.de>
```
