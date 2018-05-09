IMG_NAME=cryptorescuecore_build
NO_CACHE=false

.PHONY: clean

all:
	docker build --no-cache=$(NO_CACHE) --rm -t "$(IMG_NAME)" .
	docker run --name="$(IMG_NAME)" -d "$(IMG_NAME)" /bin/true
	docker export cryptorescuecore_build | tar --wildcards -x 'root/*.deb'
	docker rm cryptorescuecore_build
	docker rmi cryptorescuecore_build
	mv ./root/*.deb ./
	rmdir ./root

clean:
	rm *.deb
