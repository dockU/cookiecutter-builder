FROM docku/build
MAINTAINER Jon Chen <bsd@voltaire.sh>

ENV BINTRAY_USER ""
ENV BINTRAY_TOKEN ""
ENV BINTRAY_REPO ""

{% if cookiecutter.dependencies %}
RUN pacman -Syu {% for pkg in cookiecutter.dependencies.split(';') %}{{ pkg }} {% endfor %}--needed --noconfirm
{% endif %}

{% if cookiecutter.build_steps %}
{% for step in cookiecutter.build_steps.split(';') %}
RUN {{ step }}
{% endfor %}
{% endif %}

ADD build_makefile /root/Makefile
CMD ["make", "-f", "/root/Makefile", "all"]
