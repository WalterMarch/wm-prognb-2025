# Add MySQL to Outer Container

As currently set up, MySQL uses docker-compose, which does not mesh with the way the outer container is constructed.

Can docker-compose call a Dockerfile to create the rest of the outer container?