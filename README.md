![Image text](https://github.com/TenYunTech/TenYun/raw/master/tenyun/logo.jpeg)
# TenYun EcoSystem BlockChain
TenYun EcoSystem BlockChain node source code patch to bitcoin core v0.12.1

To play with TenYun node:

1, Clone bitcoin core;

    git clone https://github.com/bitcoin/bitcoin.git
    

2, Make a local branch from v0.12.1;

    cd bitcoin
    git checkout -b tenyun v0.12.1

3, Apply the patch;

    git apply tenyun.patch

4, Configure and make the command line executables;

    ./autogen.sh
    ./configure --with-gui=no --disable-debug --disable-tests --disable-wallet
    make
    cp src/bitcoind ~/tenyun
    cp src/bitcoin-cli ~/tenyun-cli

5, Start TenYun EcoSystem node;

    cd
    mkdir .tyeos
    ./tenyun -rpcuser=user -rpcpassword=123456 -daemon -onlynet=ipv4 -listenonion=0 -rpcport=28333 -datadir=.tyeos -addnode=59.110.172.243:9555 -txindex -listen=0

6, Because TenYun EcoSystem Blockchain is an opposite to a decentralized anonymous crypto currency system, you must have an secret key with an address authorized by the tenyun chain operator;

    Example:
        Authorized address: 1DxXtPEEZ71PoFbaoMScPeF1FxADfVtzhF
        Secret key wif: Ky1CCSRLVpgAGPDbm5c65vMwo21LcuACbzZ7SunK6zStP5sYDxBR

7, Import the authorized key pair as default key to the thin node;

    echo 'Ky1CCSRLVpgAGPDbm5c65vMwo21LcuACbzZ7SunK6zStP5sYDxBR 2017-08-24T06:57:54Z label=-defaultkey # addr=1DxXtPEEZ71PoFbaoMScPeF1FxADfVtzhF' > defaultkey.w
    ./tenyun-cli -datadir=.tyeos -rpcuser=user -rpcpassword=123456 -rpcconnect=127.0.0.1 -rpcport=28333 importwallet defaultkey.w

8, Now the thin node can connect to the tenyun network, data synchronization begin and you rock.

