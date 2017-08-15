# Raneto composition

This is a docker-compose composition to deploy a [Raneto](https://github.com/gilbitron/Raneto) server with [Nginx](https://github.com/nginx/nginx) reverse proxy frontend.

Alpine images are preferably used to produce really thin images (207MB raneto image and 15.5MB nginx image). 

Raneto server and nginx reverse proxy config files can be modified in the build folder. After any modification you must rebuild images with:

``` docker-compose build ```

The composition can be started with 

``` docker-compose up -d ```

Service is available on [http://localhost](http://localhost)

I would like to add a way to share volume between host and raneto docker image with unprivileged user. So it would be possible to live edit Raneto documentation.

As workarround its possible to load Markdown documentation to Raneto server with:

```docker-compose exec raneto git clone git_markdown_documentation_url example/content```

Content can be updated anytime with:

```docker-compose exec raneto  /bin/ash  example/content && git pull```