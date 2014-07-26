docker-octopress
================

Customize to your octopress project (Dockerfile)
--------------------------------------

##Locale

Set the locale of your octopress project:

    # Set correct local
    RUN locale-gen es_ES.UTF-8
    ENV LANG es_ES.UTF-8
    ENV LC_CTYPE es_ES.UTF-8


##Octopress project

Change the line in the Dockerfile to your octopress project (So we install the correct gem versions)

For example:

    RUN git clone -b source https://github.com/ticketbis/ticketbis.github.io.git octopress

To a fresh and new octopress:

    RUN git clone git://github.com/imathis/octopress.git octopress

Also is commented but if you have an octopress new fresh install you would like
to uncomment default theme installation:
    RUN rake install

Run the container
=================

Run the docker container (will be removed when exit), map localhost 4000 port to
container 4000 port, and our /home/slok/projects/ path to /home/octopress/projects
container path:

    docker run --rm -it -p 4000:4000 -v /home/slok/projects/:/home/octopress/projects slok/octopress

Example: https://asciinema.org/a/11050