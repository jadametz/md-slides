# Markdown Slides

`md-slides` is intended to be a base Docker image for building presentations.

## Usage

Content for your slides should reside in a file called `CONTENT.md`

### Your slides as a Docker image

To create a static image of your slides create the following `Dockerfile`

```
FROM jadametz/md-slides
```

Because the `Dockerfile` for `md-slides` contains an `ONBUILD` instruction, you're done! Just build your Docker image.

```shell
docker build -t <your name>/<your talk> .
```

### Developing / running your slides locally

Using a combination of `docker-compose` and volumes, you can prevent even having to build your own image while also having your content auto-update within your browser

```yml
# docker-compose.yml
version: '3'
services:
  your-talk:
    image: jadametz/md-slides
    ports:
      - 8080:80
    volumes:
      - ./CONTENT.md:/usr/share/nginx/html/CONTENT.md
```
