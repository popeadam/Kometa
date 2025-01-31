Kometa provides an extensive collection of "default" collection, overlay and playlist files.

These files provide a simple way for you to create collections/overlays/playlists based on franchises or awards or actors, etc.

The config we are working on links to two Defaults Collection Files, these lines in your config file:

```yaml
libraries:
  test_movie_lib:
    collection_files:
      - default: basic               # <<< DEFAULTS COLLECTION FILE
      - default: imdb                # <<< DEFAULTS COLLECTION FILE
```

Collections that will be created include:

  - Newly Released
  - New Episodes [TV libraries only]
  - IMDb Popular
  - IMDb Top 250
  - IMDb Lowest Rated