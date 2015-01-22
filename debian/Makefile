KEY=CD9C0E84
DIST=trusty
SRC=../elasticsearch-py
VERSION=$(shell dpkg-parsechangelog | grep Version: | cut -d' ' -f2-)
TARBALL=python-elasticsearch-1.0_$(VERSION).orig.tar.gz

clean:
	rm -fr elasticsearch-py

package:
	dpkg-buildpackage -A -us -uc
 
source:
	dpkg-buildpackage -S -k$(KEY)

source_no_sign: make_source_tarball
	dpkg-buildpackage -S -us -d
 
upload_to_ppa:
	dput ppa:lordgaav/python-elasticsearch "$(CHANGES)"

pbuild:
	pbuilder-dist "$(DIST)" "$(CHANGES)"

make_source_tarball:
	(cd $(SRC) && git checkout $(shell echo -n "$(VERSION)" | cut -d"-" -f1 )) && \
	tar zcvf ../python-elasticsearch-1.0_$(VERSION).orig.tar.gz $(SRC) --exclude="test_elasticsearch" --exclude=".git*"

unzip_source: clean
	tar xvf "../$(TARBALL)"
