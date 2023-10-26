## Note: This guide only works on ledger nanos, and your device must have sufficient space to install the app

### OS: LINUX

#### pre-requisites:

- Install docker from here : [Docker](https://docs.docker.com/engine/install/ubuntu/)

- add and reload the udev rules to allow USB access to your Ledger device:

```javascript
wget -q -O - https://raw.githubusercontent.com/LedgerHQ/udev-rules/master/add_udev_rules.sh | sudo bash
```

- Edit `Makefile`, find `COIN=bitcoin_legacy` and replace it to `COIN=blocx`, this line will use to select the app which you want to upload in your ledger nanos.

### Download Blocx-ledger

```javascript
git clone https://github.com/BLOCXTECH/app-bitcoin.git
```

- Move into that repo

```javascript
cd app-bitcoin
```

### Run below command

- It will take some time depending on your network

```javascript
sudo docker run --rm -ti --user "$(id -u):$(id -g)" --privileged -v "/dev/bus/usb:/dev/bus/usb" -v "$(realpath .):/app" ghcr.io/ledgerhq/ledger-app-builder/ledger-app-dev-tools:latest
```

- After running above command you will get new terminal, it will look something like : `bash-5.1$`

- Run below command in this terminal

```javascript
BOLOS_SDK=$NANOS_SDK

make DEBUG=1
```

- Now, below command will load blocx application to your ledger nanos

```javascript
make load
```

#### Note: During make load command, there will be some conformations in ledger.
