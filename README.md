# static-site-template

Template for static sites using Nginx to serve the content

## Example

* Generate a template:

```bash
export OPENFAAS_PREFIX=alexellis2

faas template pull https://github.com/alexellis/static-site-template
faas new --lang static-site-nginx my-homepage --prefix ${OPENFAAS_PREFIX}
```

* Add some content:

```bash
echo "<html>Hello world</html>" > ./my-homepage/index.html
```

* Deploy:

```bash
faas-cli up -f my-homepage.yml
```
