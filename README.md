** This is not an official Google product **

# Google Cloud IoT Examples for Raspbery Pi on Python
This repository contain examples how to quickly start your project on GCP using Raspberry Pi and Python.
More information about this guide can be found [here](https://lembergsolutions.com/). 

# Johnny README

Forked from: https://github.com/Ivan-koz/GC-IoT_Python_example

Tutorial: https://lembergsolutions.com/blog/rapid-hardware-prototyping-connect-your-raspberry-pi-google-cloud-iot

Copy of the tutorial is cached in `Connect Your Raspberry Pi to Google Cloud IoT.mhtml`

GCP IoT Info: https://cloud.google.com/iot/docs/create-device-registry

Include global packages with `--system-site-packages`, which already includes `RPi.GPIO`. Without `--system-site-packages`, pip install -r requirements.txt will fail with this error:

× Encountered error while trying to install package.
╰─> RPi.GPIO

```
virtualenv --system-site-packages env
```

I used the command from GCP to create an RS256 key: https://cloud.google.com/iot/docs/create-device-registry

```
openssl req -x509 -newkey rsa:2048 -keyout rsa_private.pem -nodes \
    -out rsa_cert.pem -subj "/CN=unused"
```

Also followed GCP's instruction on creating the registry and adding a device.

Read messages published to topic:

```
gcloud pubsub subscriptions pull raspberry-pi-message --auto-ack --limit=10
```