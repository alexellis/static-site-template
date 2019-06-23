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

* Access:

```bash
faas-cli describe my-homepage

Name:                my-homepage
Status:              Ready
Replicas:            1
Available replicas:  1
Invocations:         8
Image:               alexellis2/my-homepage:0.1.0
Function process:    
URL:                 http://127.0.0.1:8080/function/my-homepage
Async URL:           http://127.0.0.1:8080/async-function/my-homepage
Labels:              com.openfaas.function : my-homepage
                     com.openfaas.uid : 805258633
                     function : true
```