# crankypants

A thing that does things.

### Giving it a try via Docker

```
docker run --rm -v crankypants-data:/data hmans/crankypants
```

### Hacking on Crankypants

This currently assumes that you're on macOS. (Hacking on Crankypants on other operating systems is, of course, perfectly possible, as long as Crystal has support for them.)

```
brew bundle
shards install
yarn install
hivemind  # or any other Procfile manager

# http://localhost:3000/ (server-rendered public-facing blog)
# http://localhost:3000/app/ (your crankypants app)
```

### TODO

- [ ] Make the blog look nicer :-)
- [x] Building & overall setup
- [x] Creating posts
- [ ] Editing posts
- [x] Validate posts
- [x] Deleting posts
- [ ] Authentication
- [ ] Configuration

etc.

- [ ] Nicer validation hints in forms?
- [ ] Move database into a subdirectory (important for Docker volumes)
- [ ] CLI option to specify which database to use
- [ ] CLI option to specify which port to use

Deployment/etc.:

- [ ] https://traefik.io/
- [ ] https://github.com/umputun/nginx-le
