# our base image
FROM nobetternick/heppy:6.24.06-ubuntu20.04

RUN cd /usr/local/docker && git clone https://github.com/matplo/pyjetty.git
RUN export HEPPY_DIR=/usr/local/docker/heppy && cd /usr/local/docker/pyjetty && ./cpptools/build.sh --tenngen --tglaubermc

ENTRYPOINT [ "/usr/local/docker/fromhost/in_docker_exec.sh" ]
