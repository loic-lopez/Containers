# cmake_conan

A container that holds gcc, cmake and conan

### docker.io

see: [loiclopez/cmake_conan - Docker Image | Docker Hub](https://hub.docker.com/r/loiclopez/cmake_conan)

### ghcr.io

see: [Package cmake_conan](https://ghcr.io/loic-lopez/cmake_conan)

## Versioning scheme

The tag name is composed of three versions:
**gcc_XXX**
**cmake_XXX**
**conan_XXX**

Which is compiled as follows: `gcc_XXX-cmake_XXX-conan_XXX`

## Latest tag
The latest tag will always be the latest gcc available.

## How to use it?

Launch the following command:
```bash
docker run -it -v `pwd`:/workspace --workdir="/workspace" loiclopez/cmake_conan
```
