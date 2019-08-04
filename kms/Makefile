LOCATION=asia-northeast1 # or global
KEYRING=enc
KEYNAME=lunaword
FILENAME=plain.txt

include ../common.mk

# kmsを使えるようにする
setup:
	gcloud services enable cloudkms.googleapis.com || true
	gcloud kms keyrings create $(KEYRING) \
		--location=$(LOCATION) || true

create_key:
	gcloud kms keys create $(KEYNAME) \
		--purpose=encryption \
		--keyring=$(KEYRING) \
		--location=$(LOCATION) || true
		# --rotation-period ROTATION_PERIOD \
		# --next-rotation-time NEXT_ROTATION_TIME

encrypt:
	gcloud kms encrypt \
		--plaintext-file=$(FILENAME) \
		--ciphertext-file=$(FILENAME).enc \
		--keyring=$(KEYRING)  \
		--key=$(KEYNAME) \
		--location=$(LOCATION)

decrypt:
	gcloud kms decrypt \
		--plaintext-file=$(FILENAME).dec \
		--ciphertext-file=$(FILENAME).enc \
		--keyring=$(KEYRING)  \
		--key=$(KEYNAME) \
		--location=$(LOCATION)

rotation:
	gcloud kms keys versions create \
		--keyring=$(KEYRING) \
		--key=$(KEYNAME) \
		--location=$(LOCATION) \
		--primary

disable:
	gcloud kms keys versions disable $(VERSION) \
		--keyring=$(KEYRING) \
		--key=$(KEYNAME) \
		--location=$(LOCATION)