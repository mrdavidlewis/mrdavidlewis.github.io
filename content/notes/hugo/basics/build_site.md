---
title: "Build site"
date: 2022-11-02T15:37:15Z
draft: false
---

Prior to deploying a site you need to build it.

This process places the site which needs to be deployed in ```public```.

Publish site to ```public```:

```bash
hugo
```

Remove ```public```:

```bash
rm -r public
```

Clean up using Hugo. By default ```hugo``` leaves content in ```public``` that is not longer in ```content```. This command cleans up those orphans:
```bash
hugo --cleanDestinationDir
```


Remove and publish:
```bash
rm -r public && hugo
```


Publish and minimise:
```bash
hugo --cleanDestinationDir --minify
```
