KEY=CD9C0E84
DIST=trusty
SRC=../elasticsearch-py
VERSION=0.4.4

clean:
	rm -R elasticsearch-py

package:
	dpkg-buildpackage -A -us -uc
 
source: make_source_tarball
	dpkg-buildpackage -S -k$(KEY)

source_no_sign: make_source_tarball
	dpkg-buildpackage -S -us -d
 
upload_to_ppa:
	dput ppa:lordgaav/python-elasticsearch "$(CHANGES)"

pbuild:
	pbuilder-dist "$(DIST)" "$(CHANGES)"

make_source_tarball:
	tar zcvf ../python-elasticsearch_$(VERSION).orig.tar.gz $(SRC) --exclude="test_elasticsearch" --exclude=".git*"
