# Build Tool Docker Image

A Docker image capable defining a container capable of running the build tool must have both Python 2.7 and the JDK. Each of these exist as core images maintained by the Docker Team and available via Docker Hub ([here](https://hub.docker.com/_/python/) and [here](https://hub.docker.com/_/openjdk/)), however, as we require both, a custom image must be built. 

In order to be able to use the images maintained by the Docker Team, a script
is included that merges the two images, `create_image.sh`. Alternatively, this
script will also build the image for you.

Note: You will need a recent version of Docker. Use the Community Edition
version available at <https://store.docker.com>:

* [Mac edition](https://store.docker.com/editions/community/docker-ce-desktop-mac)
* [Windows edition](https://store.docker.com/editions/community/docker-ce-desktop-windows)
* [Other editions](https://store.docker.com/search?offering=community&type=edition)

Download it, and install it. Then, run it at least once (e.g., on the Mac,
open `/Applications/Docker.app`), which will create the various command line
links you'll need.

## To Create the `Dockerfile`

```
$ ./create_image.sh
```

## To Create the `Dockerfile` and Build the Image

```
$ ./create_image.sh build
```

## To Use the Build Tool via Docker

To run `bdc`:

```
docker run --rm -w `pwd` -e HOME=$HOME -v $HOME:$HOME build-tool bdc <YOUR> <ARGS> <HERE>
```

To run `gendbc`:

```
docker run --rm -w `pwd` -e HOME=$HOME -v $HOME:$HOME build-tool gendbc <YOUR> <ARGS> <HERE>
```

To run `master_parse`:

```
docker run --rm -w `pwd` -e HOME=$HOME -v $HOME:$HOME build-tool master_parse <YOUR> <ARGS> <HERE>
```

Alternatively, you can add the following to your aliases, in which case a native experience can be achieved:

```
alias bdc="docker run --rm -w `pwd` -e HOME=$HOME -v $HOME:$HOME build-tool bdc"
alias gendbc="docker run --rm -w `pwd` -e HOME=$HOME -v $HOME:$HOME build-tool gendbc"
alias master_parse="docker run --rm -w `pwd` -e HOME=$HOME -v $HOME:$HOME build-tool master_parse"
```