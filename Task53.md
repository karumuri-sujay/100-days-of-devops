### Task:

We encountered an issue with our Nginx and PHP-FPM setup on the Kubernetes cluster this morning, which
halted its functionality. Investigate and rectify the issue:

The pod name is `nginx-phpfpm` and configmap name is `nginx-config`. Identify and fix the problem.

Once resolved, copy `/home/thor/index.php` file from the `jump host` to the `nginx-container` within the nginx document root. After this, you should be able to access the website using `Website` button on the top bar.

`Note:` The `kubectl` utility on the `jump-host` has been configured to work with the Kubernetes cluster.

#### Solution:

`kubectl get pod nginx-phpfpm -o yaml > nginx-phpfpm.yml`

Update mountPath to` /var/www/html`

Delete and start the pod
