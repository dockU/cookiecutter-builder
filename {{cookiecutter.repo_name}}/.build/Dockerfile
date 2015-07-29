FROM docku/build
MAINTAINER Jon Chen <bsd@voltaire.sh>

ENV BINTRAY_USER ""
ENV BINTRAY_TOKEN ""
ENV BINTRAY_REPO ""

RUN pacman -Syu {{ cookiecutter.dependencies }}--needed --noconfirm

RUN {{ cookiecutter.build_steps }}

ADD build_makefile /root/Makefile
CMD ["make", "-f", "/root/Makefile", "all"]
