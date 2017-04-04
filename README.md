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

Here's a listing of the environment's packages:

```bash
$ pip list
appdirs (1.4.3)
boto3 (1.4.4)
botocore (1.5.34)
CacheControl (0.12.2)
click (6.7)
click-plugins (1.0.3)
cligj (0.4.0)
docutils (0.13.1)
iso3166 (0.8)
jmespath (0.9.2)
mapbox (0.11.0)
mapboxcli (0.6.0)
msgpack-python (0.4.8)
packaging (16.8)
pip (9.0.1)
polyline (1.3.2)
pyparsing (2.2.0)
python-dateutil (2.6.0)
requests (2.13.0)
s3transfer (0.1.10)
setuptools (34.3.3)
six (1.10.0)
uritemplate (3.0.0)
wheel (0.29.0)
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
