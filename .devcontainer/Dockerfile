FROM python:3.11-bullseye

ENV PDM_USE_VENV=False \
    # Required to make Python find packages when using PDM's PEP582 mode
    PYTHONPATH=/home/dev/.local/lib/python3.11/site-packages/pdm/pep582

RUN apt update \
    # Install deps
    && apt install -y \
        sudo \
    # Setup a non-root user
    && useradd -ms /bin/bash dev \
    && adduser dev sudo \
    && echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers \
    # Configure necessary dirs with appropriate perms
    && mkdir /static \
    && chown -R dev:dev /static

USER dev:dev
RUN pip install --user pdm==2.4.9

EXPOSE 8000
