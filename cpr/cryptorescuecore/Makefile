all:
	git clone https://github.com/cryptorescue-project/cryptorescuecore
	cd cryptorescuecore && git checkout master
	cd cryptorescuecore && rm -rf .git # Delete .git folder to reduce space
	cd cryptorescuecore && npm install --production
	rm -rf cryptorescuecore/node_modules/cryptorescuecore-node/bin/*.gz
	rm -rf cryptorescuecore/node_modules/cryptorescuecore-node/bin/cryptorescue-*/bin/cryptorescue-qt
	rm -rf cryptorescuecore/node_modules/cryptorescuecore-node/bin/cryptorescue-*/bin/test_cryptorescue
	rm -rf cryptorescuecore/node_modules/cryptorescuecore-node/test/*

clean:
	rm -fr cryptorescuecore
