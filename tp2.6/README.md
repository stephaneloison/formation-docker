docker run --rm -v $(pwd):/tmp busybox find /tmp -name "*e1*"

docker run --rm -v $(pwd):/tmp busybox /bin/sh -c "cd /tmp; find . -name '*e1*"

docker run --rm -it -v $(pwd):/tmp busybox sh

