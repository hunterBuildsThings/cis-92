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

## Deployment Instructions

To deploy the application to your Kubernetes cluster, follow these steps:

1. **Apply the files in deployment directory**: Run the following command in when in the deployment directory
   ```bash
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
   kubectl delete -f .
   ```