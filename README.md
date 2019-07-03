# OwnBlockchainSdkJVM

Own Blockchain SDK for JVM

## Quick Start

```bash
$ git clone https://github.com/OwnMarket/OwnBlockchainSdkJVM.git
$ cd Source
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
    <version>1.0.2</version>
</dependency>
```

Use the package in Java code

```java

import com.weown.blockchain.sdk.Tx;
import com.weown.blockchain.sdk.Wallet;

class Program {

    public static void main(String[] args) {
        String networkCode = "OWN_PUBLIC_BLOCKCHAIN_TESTNET";

        // Create a new wallet
        Wallet wallet = new Wallet();
        System.out.println(String.format("PK: %s, Address: %s", wallet.getPrivateKey(), wallet.getAddress()));

        // Compose a transaction with nonce = 1
        Tx tx = new Tx(wallet.getAddress(), 1);
        tx.setActionFee(0.01f); // Set action fee.
        tx.addTransferChxAction("CHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx", 100); // Transfer 100 CHX to CHxxx... address.

        // Look at the raw transaction in JSON format
        System.out.println(tx.toJson(true));

        // Sign the transaction for submission to node API on TestNet
        System.out.println(tx.sign(networkCode, wallet.getPrivateKey()).toJson(false));
    }
}
```
