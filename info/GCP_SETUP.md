1. go to gcp and create account

2. go to link and activate billing account (tarjeta; vale una sin dinero)
   https://console.cloud.google.com/billing

3. meterse al proyecto. Te crea un 'My First Project', ese te vale.

gcloud config set project PROJECT_ID

# 1. Dar permiso para construir (Cloud Build)

gcloud projects add-iam-policy-binding PROJECT_ID \
 --member=serviceAccount:SERVICE_ACCOUNT_EMAIL \
 --role=roles/cloudbuild.builds.builder

# 2. Dar permiso para escribir archivos temporales (Storage)

gcloud projects add-iam-policy-binding PROJECT_ID \
 --member=serviceAccount:SERVICE_ACCOUNT_EMAIL \
 --role=roles/storage.objectAdmin

# 3. Activar vertex api y darle permiso

gcloud services enable aiplatform.googleapis.com --project PROJECT_ID

gcloud projects add-iam-policy-binding PROJECT_ID \
 --member=serviceAccount:SERVICE_ACCOUNT_EMAIL \
 --role=roles/aiplatform.user

gcloud services enable run.googleapis.com

gcloud services enable artifactregistry.googleapis.com cloudbuild.googleapis.com

5. desplegar en cloud run! (a mi me gusta con un deploy.sh desde consola por facilidad)
   bash deploy.sh

   (cambiar en la primera linea el project id)
