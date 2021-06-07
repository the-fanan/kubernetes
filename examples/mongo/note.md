HANDLING SECRET
=================
The mongodb requires env variables of username and password. These are sensitive data so have to be handled via **Secret**

If a deployment is going to reference a secret, the secret must be created before the deployment. The same thing goes for config maps.