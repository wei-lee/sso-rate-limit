This repo shows how to add a Nginx sidecar container to the Keycloak pod to control the request limit to Keycloak.

## Steps

1. Create the Nginx configuration. This repo provides [an example](./nginx.conf). It assumes the Keycloak instance is deployed withou SSL. You can use it as a base and modify it to work with your Keycloak set up. For more information about how to configure rate limiting using Nginx, please checkout this [document](https://www.nginx.com/blog/rate-limiting-nginx/?_ga=2.149661558.1565318143.1596549227-433760022.1596211781). 
2. Create a configmap for using the Nginx configuration:
   ```
   oc create cm nginx-conf --from-file=nginx.conf=./nginx.conf -n keycloak
   ```
3. 