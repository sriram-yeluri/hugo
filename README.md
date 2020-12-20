# hugo 0.79.1
Repository created to build docker image with hugo for static site generation

## Building the image

```sh
docker build -t yeluris/hugo:0.79.1 .
```

## Using the image

Using the image as a stand-alone image:

```sh
docker run -p 1313:1313 yeluris/hugo:0.79.1
```
This will automatically start hugo server, and your site is now available on http://localhost:1313.

If you are using boot2docker, you need to adjust the base URL:

```sh
docker run -p 1313:1313 -e HUGO_BASE_URL=http://YOUR_DOCKER_IP:1313 yeluris/hugo:0.79.1
```

The image is also suitable for use as a volume image for a web server, such as nginx

```sh
docker run -d -v /usr/share/nginx/html --name site-data yeluris/hugo:0.79.1
docker run -d --volumes-from site-data --name site-server -p 80:80 nginx
```
