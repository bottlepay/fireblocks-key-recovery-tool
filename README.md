# Fireblocks recovery key utility

## Installation

* Please clone the repository:
  * `git clone https://github.com/fireblocks/fireblocks-key-recovery-tool.git`

* cd fireblocks-key-recovery-tool

### Prerequisites

* Backup file `<backup.zip>`
* Private key `<key.pem>`
* Passphrase

## YubiHSM Support

Decryption operations may utilise RSA private keys stored on a YubiHSM device.

This functionality is enabled by setting the `--yubihsm-url` flag to either a yubihsm-connector URL or USB device connection string.
The Authentication Key ID to use may be set using `--yubihsm-authkey`, which defaults to `1`.

Once YubiHSM mode is enabled, parameters that normally expect a local private key PEM path will instead treat the value as an Asymmetric Key ID.

## Running in Docker

### Build the utility in docker
* docker build -t fb_recover_key .

### Run the utility in docker
* cd to `<directory containing the backup file and the private key>`
* Run: docker run -it -v "${PWD}:/opt/fb_recover_keys/backup" fb_recover_key:latest bash
* Run: ./fb_recover_keys.py backup/backup.zip backup/key.pem --prv

## Running Locally

### Build the utility locally
* install python 3
* install pip 3
* run: pip3 install -r requirements.txt

### Run the utility locally
* ./fb_recover_keys.py `<backup zip file> <RSA recovery private key>` --prv

### Run the utility locally utilising a YubiHSM device
* ./fb_recover_keys.py --yubihsm-url `http://localhost:12345 <backup zip file> <hsm asymmetric key id>`  --prv
