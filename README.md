# Encuentra el error

El objetivo de esta práctica es encontrar el problema que tenemos en nuestra aplicación.

### Kubernetes clúster

Para hacer esta práctica necesitas un clúster de Kubernetes. Si no dispones de uno, puedes usar `minikube`, aquí puedes seguir las instrucciones de instalación:

    https://minikube.sigs.k8s.io/docs/start/

Para interactuar con el clúster vas a necesitar `kubectl` también:

    https://kubernetes.io/docs/tasks/tools/

Una vez instalado `kubectl` y `minikube`, arráncalo:

    minikube start


### Depliega los ficheros de ejemplo

Para desplegar los ficheros de ejemplo, clona este repositorio, entra dentro del mismo y ejecuta:

    kubectl apply -f .

### Comprueba que los pods están corriendo:

    kubectl get po
    NAME                      READY   STATUS        RESTARTS   AGE
    apache-6fb77f6c95-2mmt6   1/1     **Running**   0          44s
    nginx-589746f7b9-5c89c    1/1     **Running**   0          44s

### Accede al servicio nginx

Accedamos a nuestro nginx:

    minikube service nginx

Aquí puedes acceder desde el navegador o curl. Refresca el navegador varias veces o ejecuta curl varias veces:

    $ curl http://127.0.0.1:55028
    <html><body><h1>It works!</h1></body></html>


    $ curl http://127.0.0.1:55028
    <!DOCTYPE html>
    <html>
    <head>
    <title>Welcome to nginx!</title>
    <style>
        body {
            width: 35em;
            margin: 0 auto;
            font-family: Tahoma, Verdana, Arial, sans-serif;
        }
    </style>
    </head>
    <body>
    <h1>Welcome to nginx!</h1>
    <p>If you see this page, the nginx web server is successfully installed and
    working. Further configuration is required.</p>

    <p>For online documentation and support please refer to
    <a href="http://nginx.org/">nginx.org</a>.<br/>
    Commercial support is available at
    <a href="http://nginx.com/">nginx.com</a>.</p>

    <p><em>Thank you for using nginx.</em></p>
    </body>
    </html>

Verás que algunas veces responde nginx y otras apache.

Tu objetivo es encontrar el por qué no es `nginx` el único que responde. Como requisito, `nginx` y `apache` **deben** estar corriendo. 