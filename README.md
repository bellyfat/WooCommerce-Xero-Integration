# WooCommerce-Xero-Integration
A simple Python utility that uses the Xero API and the WC API to keep product and customer data in sync.

## Setup Instructions

### Set up Xero API

Follow these instructions to set up a private Xero application using a public / private key pair: https://developer.xero.com/documentation/getting-started/private-applications/
Copy the client key and secret from the api manager into a copy of the example xero yaml config file along with the path to the private key file you generated

### Set up WC API

Follow instructions for generating your client key / secret pair from WooCommerce
Copy the client key and secret from the WooCommerce into a copy of the example wc yaml config file along with the store url

### Install instructions for debian-based linux
If running ubuntu, you need to perform these extra steps:
```bash
sudo apt-get install python-pip python-dev libxml2-dev libxslt1-dev libz-dev libffi-dev
```

### Set up Application dependencies

Install python2 and pip then install the dependencies with pip2:

```bash
pip2 install -r requirements.txt
```

### Fix for Ubuntu JWT

If you ever see something like :
```
File ...jwk.py", line 60
def is_sign_key(self) -> bool:
SyntaxError: invalid syntax
```

Try this:
```
pip uninstall jwt
pip install pyjwt
```

### Fix for Ubuntu OpenSSL

If you ever see something like:
```
fatal error: openssl/opensslv.h: No such file or directory
```
The fix is:
```
sudo apt-get install python-pip python-dev libffi-dev libssl-dev libxml2-dev libxslt1-dev libjpeg8-dev zlib1g-dev
pip install cryptography
```

### Fix for Ubuntu Cryptography
If you see something like:
```
ImportError: No module named Crypto.PublicKey
```
the fix is:
```shell
pip install pycrypto
```

## Install Instructions for Windows
### Creating shortcut
Create a shortcut to

`C:\Windows\System32\bash.exe -c "cd /mnt/c/Users/User/Documents/GitHub/WooCommerce-Xero-Integration && ./sync.sh"`

## Usage

```
python main.py --download-wc --download-xero --wc-config-file=wc_api.yaml --xero-config-file=xero_api.yaml
```
