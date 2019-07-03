# OwnBlockchainSdkJVM

Own Blockchain SDK for JVM

## Quick Start

```bash
$ git clone https://github.com/OwnMarket/OwnBlockchainSdkJVM.git
$ cd own-blockchain-sdk
$ mvn compile
```

```bash
$ mvn test
```

## Usage

Own Blockchain SDK for Java can be used as a Maven package.
Add in your ```pom.xml``` the following dependency 
```xml
<dependency>
    <groupId>com.weown</groupId>
    <artifactId>own-blockchain-sdk</artifactId>
    <version>1.0.1</version>
</dependency>
```

Use the package in Java code

```java

import com.weown.blockchain.sdk.Wallet;
import com.weown.blockchain.sdk.Tx;

class Program {

    public static void main(String[] args) {
        String networkCode = "OWN_PUBLIC_BLOCKCHAIN_TESTNET";

        // Create a new wallet
        Wallet wallet = new Wallet();
        System.out.println(String.format("PK: %s, Address: %s", wallet.getPrivateKey(), wallet.getAddress()));

        // Compose a transaction with nonce = 1
        Tx tx = new Tx(wallet.Address, 1);
        tx.ActionFee = 0.01m; // Set action fee.
        tx.AddTransferChxAction("CHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx", 100); // Transfer 100 CHX to CHxxx... address.    

        // Look at the raw transaction in JSON format
        System.out.println(tx.toJson(true));

        // Sign the transaction for submission to node API on TestNet
        System.out.println(tx.sign(networkCode, wallet.getPrivateKey()).toJson(false));        
    }    
}
```
