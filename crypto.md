### Crypto Mining

#### Necessary libraries
```bash
sudo apt install git build-essential cmake libuv1-dev libssl-dev libhwloc-dev
#for termux setup we only need build-essential and cmake
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
cmake .. #for termux setup cmake .. -DWITH_HWLOC=OFF
make #for termux setup make -j10
```

#### Start mining
```bash
sudo ./xmrig -o pool.id -u wallet.id -p device
```
a pool example would be "gulf.moneroocean.stream:10128"
