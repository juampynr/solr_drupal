# Apache Solr 1.4 for Drupal's apachesolr module

https://www.drupal.org/project/apachesolr requires Apache Solr
1.4 or 3.5. These two have compilation issues with the Java version
that comes with Ubuntu 16.

If you find compilation errors while running Solr locally,
try this image instead.

The Solr server at the image already contains the configuration
files referenced at the [Drupal module's README](http://cgit.drupalcode.org/apachesolr/tree/solr-conf/solr-1.4)
so you should be ready to install apachesolr module, open
`config/search/apachesolr/settings/solr/edit` and set
`http://0.0.0.0:8983/solr` as the Solr server.

## Usage

```bash
# First run: downloads the image and makes it available at http://0.0.0.0:8983/solr.
docker run -it --name=solr_drupal -p 8983:8983 juampynr/solr_drupal

# Stop the server
docker stop solr_drupal

# Start again the server (keeping the index data from the previous run)
docker start solr_drupal
```

Happy indexing!

## Debugging
While the container is running, you can enter it in a different terminal
with the following command:

```bash
docker exec -it solr_drupal bash
```
