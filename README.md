# wordpress-container
Automatically built static / updates-via-reploy wordpress container images

Bitnami stopped updating their wordpress container images which were static images. I tried to look for similar images but I couldn't find any, so here is my version.

For full image description and usage information go to: https://github.com/docker-library/docs/tree/master/wordpress

This repo just follows the apache version for now.

## Additional notes

You might want to mount your already existing `wp-content` folder to `/usr/src/wordpress/wp-content`.

Also you should run this image in read-only, providing writeable storage for `/tmp`, `/run`, and (optionally) `wp-content/uploads`:
```console
$ docker run ... \
	--read-only \
	--tmpfs /tmp \
	--tmpfs /run \
	--mount type=...,src=...,dst=/usr/src/wordpress/wp-content/uploads \
	... \
	--env WORDPRESS_DB_HOST=... \
	--env WORDPRESS_AUTH_KEY=... \
	--env ... \
	pushrbx/wordpress-container:tag
```
