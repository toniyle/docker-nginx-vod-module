nginx-vod-module-docker
=======================

This repository contains a Dockerfile for building nginx with [Kaltura's
vod-module](https://github.com/kaltura/nginx-vod-module).

Building locally
----------------

This repository uses Docker's multi-stage builds, therefore building this image
requires Docker 17.05 or higher. Given that you have all the required
dependencies, building the image is as simple as running a ``docker build``:

```
docker build -t nginx-vod-module .
```

run from nginx-vod-module-docker -directory using example media files
````
cd examples && 
docker run -p 8080:80 -v `pwd`/videos:/opt/static/videos -v `pwd`/nginx.conf:/usr/local/nginx/conf/nginx.conf --rm  nginx-vod-module
````
Run browser on used port eg. with url to test files
- HLS
```
http://localhost:8080/hls/devito,360p.mp4,480p.mp4,720p.mp4,.en_US.vtt,.urlset/master.m3u8
```
- DASH
```
http://localhost:8080/dash/devito,360p.mp4,480p.mp4,720p.mp4,.en_US.vtt,.urlset/manifest.mpd
```
 - DASH.IF Reference player
 ```
 https://reference.dashif.org/dash.js/nightly/samples/dash-if-reference-player/index.html?mpd=http%3A%2F%2Flocalhost%3A8080%2Fdash%2Fdevito%2C360p.mp4%2C480p.mp4%2C720p.mp4%2C.en_US.vtt%2C.urlset%2Fmanifest.mpd
 ```

Docker Hub
----------

The ORGINAL image is available on Docker Hub: https://hub.docker.com/r/nytimes/nginx-vod-module/.
