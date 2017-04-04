# mapbox-cli-benchmarks
Mapbox CLI benchmarking

There is significant overhead to using setuptools entry points. See
https://github.com/pypa/setuptools/issues/510. This project contains research
into the effects on the Mapbox CLI and how to make it faster.

### Installation

Install the mapboxcli package in a new environment. I've used
virtualenvwrapper and Python 3.6.

```bash
$ mkvirtualenv -r requirements.txt -p /usr/local/bin/python3.6
mapbox-cli-benchmarks
```

### Python start-up

No scan of setuptools entry points.

```bash
$ time python -c "import mapboxcli"

real    0m0.020s
user    0m0.015s
sys     0m0.004s
```

### Mapbox CLI

The environment is scanned for setuptools entry points.

```bash
$ time mapbox --help >& /dev/null

real    0m0.481s
user    0m0.431s
sys     0m0.042s
```
