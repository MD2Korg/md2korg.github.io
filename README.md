Edit `mkdocs` files in the `dev` branch

Travis CI is utilized to push commits to `dev` onto the public webpage.

Manual deployment is possible, but not necessary, to Github pages with:
```
mkdocs gh-deploy -c -b master
```


# Reference

- Markdown is supported
- Codehilite is utilized for syntax highlightiing
- [Admonition](https://pythonhosted.org/Markdown/extensions/admonition.html)

```
!!! warning "Message"
  Details...
```

```
!!! note "Message"
  Details...
```
