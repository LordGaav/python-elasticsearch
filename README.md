python-elasticsearch
--------------------

This repository contains debian control files for creating a python-elasticsearch Ubuntu package for precise/saucy/trusty.

This branch will build the 1.0.0 version of python-elasticsearch.


Building
========

To build this package, I suggest using pbuilder-dist:

1. Checkout the 1.0.0 branch of [elasticsearch-py] next to python-elasticsearch.
2. Install pbuilder: `apt-get install ubuntu-dev-tools debhelper`.
3. Create a pbuilder environment for Trusty Tahr: `pbuilder-dist trusty create`.
4. Create the source package and .dsc file: `make -f debian/Makefile source_no_sign`.
5. Create the package using pbuilder-dist:  `make -f debian/Makefile pbuild CHANGES=../python-elasticsearch_<VERSION>.dsc`.

OR

1. Install my PPA and install the package: `add-apt-repository ppa:lordgaav/python-elasticsearch && apt-get update && apt-get install python-elasticsearch-1.0`.

[elasticsearch-py]: https://github.com/elasticsearch/elasticsearch-py/tree/1.0.0
