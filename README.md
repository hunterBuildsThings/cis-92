| Variable Name | Default Value | Description |
| --- | --- | --- |
| PORT | 8080 | The network port the application listens on for incoming traffic. |
| STUDENT_NAME | hunter martinez | Name of the student |
| SITE_NAME | www.cis92.com | Name of the site |
| DATA_DIR | /data | Directory where db is stored |
| DEBUG | 1 | 1 turns debug mode on and 0 turns it off |
| SECRET_KEY | this-is-a-bad-key | A unique, cryptographically strong key used for cryptographic signing and protecting sessions and CSRF tokens. |
| DJANGO_SUPERUSER_NAME | admin | Name of the superuser account for logging into web ui |
| DJANGO_SUPERUSER_EMAIL | admin@admin.com | Email of the superuser account |
| DJANGO_SUPERUSER_PASSWORD | password | Password of the superuser account |

## values-postgres.yaml
There are default authentication credentials in the values-postgres.yaml file that should be changed before application is deployed.

| Variable Name | Default Value | Description |
| --- | --- | --- |
| username | mysiteuser | username |
| password | this-is-a-bad-password | password |
| database | mysite | name of database |

Additionally GKE Autopilot resource requests and limits can
be changed from the default values for `memory`, `cpu`, and `ephemeral-storage`

## Deployment Instructions

To deploy the application to your Kubernetes cluster, follow these steps:

1. **Apply the files in deployment directory**: Run the following command in when in the deployment directory
   ```bash
   helm install postgres oci://registry-1.docker.io/bitnamicharts/postgresql --values values-postgres.yaml

   kubectl apply -f .
   ```
2. **Find the external IP address**: Use the following command and wait until 
pod spins up and copy the external IP address and paste it in the browser to view 
the application.
   ```bash
   watch kubectl get all
   ```

## Deletion Instructions

To remove the application and its associated resources from the cluster, run the following steps in the deployment directory:

1. **Delete the Deployment and Services**:
   ```bash
   helm uninstall postgres
   kubectl delete -f .
   ```


   ## Scaling Locust Results

   | Replicas | Requests per second | CPU Utilization | Memory utilization |
   | --- | --- | --- | --- |
   | 1 | 15.56 | 99% | 9% |
   | 2 | 24.12 | 73.5% | 9% |
   | 3 | 31.84 | 55.3% | 9% |
   | 4 | 35 | 42.75% | 8.5% |
   | 5 | 37.7 | 34.4% | 8.25% |