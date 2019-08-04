PROJECT_NAME=test-proj
COMPUTE_ZONE=asia-northeast1-a

include ../common.mk

setup:
	gcloud config configurations create mytest
	gcloud config set project ${PROJECT_NAME}
	gcloud config set compute/zone ${COMPUTE_ZONE}
	gcloud auth login

switch:
	gcloud config configurations activate $(configname)