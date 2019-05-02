<nav class="top-nav" data-js-no-preview="" role="navigation">

<div class="container">

[MindSecurity.org](https://mindsecurity.org/)

<div class="actions">

*   [<span class="text"></span>](https://www.facebook.com/sharer/sharer.php?u=https://devhints.io/docker-compose.html)
*   [<span class="text"></span>](https://twitter.com/intent/tweet?text=The%20ultimate%20cheatsheet%20for%20docker-compose.%20https://devhints.io/docker-compose.html)

*   [<span class="text -visible">Link</span>](https://github.com/rstacruz/cheatsheets/blob/master/docker-compose.md)

</div>

</div>

</nav>

<div class="body-area">

<header class="main-heading -center" role="banner">

# docker-compose _cheatsheet_

<div class="adbox" data-js-no-preview="">

<div class="ad -codefund" role="complementary">

<aside class="codefund-sponsor" data-js-no-preview=""></aside>

</div>

</div>

</header>

<main class="post-content MarkdownBody" data-js-main-body="" data-js-anchors="" role="main">

### Basic example

    # docker-compose.yml
    version: '2'

    services:
      web:
        build: .
        # build from Dockerfile
        context: ./Path
        dockerfile: Dockerfile
        ports:
         - "5000:5000"
        volumes:
         - .:/code
      redis:
        image: redis

### Commands

    docker-compose start
    docker-compose stop

    docker-compose pause
    docker-compose unpause

    docker-compose ps
    docker-compose up
    docker-compose down

## Reference

### Building

    web:
      # build from Dockerfile
      build: .

      # build from custom Dockerfile
      build:
        context: ./dir
        dockerfile: Dockerfile.dev

      # build from image
      image: ubuntu
      image: ubuntu:14.04
      image: tutum/influxdb
      image: example-registry:4000/postgresql
      image: a4bc65fd

### Ports

      ports:
        - "3000"
        - "8000:80"  # guest:host

      # expose ports to linked services (not to host)
      expose: ["3000"]

### Commands

      # command to execute
      command: bundle exec thin -p 3000
      command: [bundle, exec, thin, -p, 3000]

      # override the entrypoint
      entrypoint: /app/start.sh
      entrypoint: [php, -d, vendor/bin/phpunit]

### Environment variables

      # environment vars
      environment:
        RACK_ENV: development
      environment:
        - RACK_ENV=development

      # environment vars from file
      env_file: .env
      env_file: [.env, .development.env]

### Dependencies

      # makes the `db` service available as the hostname `database`
      # (implies depends_on)
      links:
        - db:database
        - redis

      # make sure `db` is alive before starting
      depends_on:
        - db

### Other options

      # make this service extend another
      extends:
        file: common.yml  # optional
        service: webapp

      volumes:
        - /var/lib/mysql
        - ./_data:/var/lib/mysql

## Advanced features

### Labels

    services:
      web:
        labels:
          com.example.description: "Accounting web app"

### DNS servers

    services:
      web:
        dns: 8.8.8.8
        dns:
          - 8.8.8.8
          - 8.8.4.4

### Devices

    services:
      web:
        devices:
        - "/dev/ttyUSB0:/dev/ttyUSB0"

### External links

    services:
      web:
        external_links:
          - redis_1
          - project_db_1:mysql

### Hosts

    services:
      web:
        extra_hosts:
          - "somehost:192.168.1.100"

### Network

    # creates a custom network called `frontend`
    networks:
      frontend:

### External network

    # join a pre-existing network
    networks:
      default:
        external:
          name: frontend

</main>

</div>

<section class="comments-area" id="comments" data-js-no-preview="">


### Other Devops cheatsheets

*   [**AWS CLI** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/awscli)
*   [**Chef** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/chef)
*   [**CircleCI** <span>cheatsheet</span>](https://devhints.io/circle)
*   [**Deis** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/deis)
*   [**Docker CLI** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/docker)
*   [**Dockerfile** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/dockerfile)

</div>

</div>

<div class="group">

<div class="related-posts-group">

### Top cheatsheets

*   [**Elixir** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/elixir)
*   [**ES2015+** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/es6)
*   [**React.js** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/react)
*   [**Vimdiff** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/vim-diff)
*   [**Vim** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/vim)
*   [**Vim scripting** <span>cheatsheet<abbr class="attribute-peg -new-layout hint--bottom" data-hint="New layout!"><span></span></abbr></span>](https://devhints.io/vimscript)

</div>

</div>

</div>

</div>

</footer>
