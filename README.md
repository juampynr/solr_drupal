# Apache Solr 1.4 for Drupal's apachesolr module

https://www.drupal.org/project/apachesolr requires Apache Solr
1.4 or 3.5. These two have compilation issues with the Java version
that comes with Ubuntu 16.

If you find compilation errors while running Solr locally,
try this image instead.

## Installation and first run

Run the image with the following command:

```bash
docker run -it --name=solr_drupal -p 8983:8983 juampynr/solr_drupal
```

Then, open it in your browser at `http://0.0.0.0:8983/solr/admin`.

The Solr server at the image already contains the configuration
files referenced at the [Drupal module's README](http://cgit.drupalcode.org/apachesolr/tree/solr-conf/solr-1.4)
so you should be ready to install apachesolr module, open
`config/search/apachesolr/settings/solr/edit` and set
`http://0.0.0.0:8983/solr` as the Solr server.

Happy indexing!

## Future runs (so the index is kept)

The `docker run` command from the above section created a container. If you
already indexed some content and want to keep it, the next time that you
want to start the Solr server don't use `docker run` but instead simply
restart the container with the following command:

```bash
docker start solr_drupal
``` 

## Debugging
While the container is running, you can enter it in a different terminal
with the following command:

```bash
docker exec -it solr_drupal bash
```
