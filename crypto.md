### Crypto Mining

#### Necessary libraries
```bash
sudo apt install git build-essential cmake libuv1-dev libssl-dev libhwloc-dev
```

#### Clone the mining software
```bash
git clone https://github.com/xmrig/xmrig.git
```

#### Preperation
```bash
cd xmrig
mkdir build
cd build
cmake ..
make
```

#### Start mining
```bash
sudo ./xmrig -o pool.id -u wallet.id -p device
```
a pool example would be "gulf.moneroocean.stream:10128"
