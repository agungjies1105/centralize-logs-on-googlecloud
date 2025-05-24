# Audit Log Management on Google Cloud & Notification using Cloud Run Function

Audit Log Management is how we can Centralizing audit logs in Google Cloud is a crucial practice for security monitoring, compliance, and operational insights. By consolidating logs from various projects and services into a single, manageable location, organizations can enhance their security posture and simplify analysis. This guide outlines the key concepts and steps to effectively centralize your audit logs on Google Cloud.

## Prerequisite
1. You Must setup Organization with Domain and you have an access to create and manage Organization Folder
2. You Must have an Access to Organization Policy Administrator to Remove Prevent Unauthorized Access to Cloud Run Function
3. You Must have an Access to Create New Project and working under Organization

## Setup Environment
1. Create new Folder Under Organization and Assign the project inside the folder
2. Create new project "Central Log Management" to be used as Centralized Logging

## Setup Log Router in Folder 
1. Go to Project "Central Log Management"
2. Create Logging Bucket :  
gcloud logging buckets update BUCKET_NAME \
   --location=LOCATION --project=PROJECT_ID \
   --retention-days=365
3. Create Log Sink in Folder Level
gcloud logging sinks create SINK_NAME \
logging.googleapis.com/projects/PROJECT_ID  \
  --log-filter='logName:cloudaudit.googleapis.com' \
  --description="Audit logs from my organization" \
  --include-children
4. Setup IAM Roles Created to Central Log Management Project and Grant Permission
5. 

