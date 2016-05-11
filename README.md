Edit `mkdocs` files in the `dev` branch

Travis CI is utilized to push commits to `dev` onto the public webpage.

Manual deployment is possible, but not necessary, to Github pages with:
```
mkdocs gh-deploy -c -b master
```
