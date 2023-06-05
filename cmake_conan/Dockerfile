ARG GCC_VERSION

FROM gcc:${GCC_VERSION} as cmake_builder

WORKDIR /tmp

ARG CMAKE_VERSION

ENV CMAKE_INSTALL_DIR=/opt/cmake
RUN wget https://github.com/Kitware/CMake/releases/download/v${CMAKE_VERSION}/cmake-${CMAKE_VERSION}-linux-x86_64.sh
RUN mkdir -p ${CMAKE_INSTALL_DIR}
RUN bash cmake-${CMAKE_VERSION}-linux-x86_64.sh --skip-license --prefix=${CMAKE_INSTALL_DIR}

FROM gcc:${GCC_VERSION}

LABEL org.opencontainers.image.source="https://github.com/loic-lopez/Containers"
LABEL org.opencontainers.image.authors="Loïc LOPEZ"
LABEL org.opencontainers.image.title="cmake_conan"

# install deps (python and cmake)
RUN apt-get update && apt-get install python3-dev python3-pip --no-install-recommends -y && apt-get clean

ENV CMAKE_INSTALL_DIR=/opt/cmake
COPY --from=cmake_builder ${CMAKE_INSTALL_DIR} ${CMAKE_INSTALL_DIR}
ENV PATH=${CMAKE_INSTALL_DIR}/bin:$PATH

ARG CONAN_VERSION
RUN pip install --no-cache-dir -Iv conan==${CONAN_VERSION}

RUN g++ -v && \
    gcc -v && \
    gcov -v && \
    make -v && \
    cmake --version && \
    conan --version
