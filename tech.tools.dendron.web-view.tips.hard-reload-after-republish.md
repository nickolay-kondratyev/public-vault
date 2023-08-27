---
id: msg5bdi3p8lf67ygnqripeh
title: Hard Reload after Republis
desc: ''
updated: 1675744194478
created: 1675558978523
---

After republishing your Dendron web-view the old content might still show. YAnd you might have to run `Hard Reload`. You can see hard reload option in chrome when you activate the `Inspect` view.

![img](/assets/images/Screenshot_2023-02-04_at_5.04.06_PM.png){max-width: 500px, display: block, margin: 0 auto}

![img](/assets/images/Screenshot_2023-02-04_at_5.04.44_PM.png){max-width: 500px, display: block, margin: 0 auto}

## To test

This might work as well:
```shell
rm -rf ~/Library/Caches/Google/Chrome/Default/Cache/Cache_Data
```