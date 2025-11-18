# end-to-end-breast-cancer-classification-using-cnn
end-to-end-breast-cancer-classification-using-cnn

to execute the api you have to : 
execute api/main.py 

to do the prediction by using a frontend , you have to : 
in the terminal , execute this commands: 
cd frontend 
npm install --from-lock-json 
npm audit fix 
you have to change env.exemple to env, 
export NODE_OPTIONS=--openssl-legacy-provider 
npm run start

to execute with GCP :
 Deploying the TF Model (.h5) on GCP
Create a GCP account.
Create a Project on GCP (Keep note of the project id).
Create a GCP bucket.
Upload the tf .h5 model generate in the bucket in the path models/potato-model.h5.
Install Google Cloud SDK (Setup instructions).
Authenticate with Google Cloud SDK.
gcloud auth login
Run the deployment script:
cd gcp
gcloud projects describe breast-classification-object --format="value(projectNumber)"
bash pemission.sh
gcloud functions deploy predict --gen2 --region=europe-west1 --runtime=python313 --entry-point=predict --trigger-http --allow-unauthenticated --memory=2048MB  --timeout=540s --project=breast-classification-object

Your model is now deployed.
Use Postman to test the GCF using the Trigger URL.

don't forget to update : BUCKET_NAME , PROJECT_NUMBER,PROJECT_ID, class_names , model