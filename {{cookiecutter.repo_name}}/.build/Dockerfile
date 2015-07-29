FROM docku/build
MAINTAINER Jon Chen <bsd@voltaire.sh>

ENV BINTRAY_USER ""
ENV BINTRAY_TOKEN ""
ENV BINTRAY_REPO ""

RUN pacman -Syu {% for pkg in cookiecutter._dependencies %}{{ pkg }} {% endfor %}--needed --noconfirm

{% for step in cookiecutter._build_steps %}
RUN {{ step }}
{% endfor %}

ADD build_makefile /root/Makefile
CMD ["make", "-f", "/root/Makefile", "all"]
