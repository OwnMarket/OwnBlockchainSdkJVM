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
```bash
<dependency>
    <groupId>com.weown</groupId>
    <artifactId>own-blockchain-sdk</artifactId>
    <version>1.0.0</version>
</dependency>
```

Use the package in Java code

```bash
class Program {

    public static void main(String[] args) {
        String networkCode = "OWN_PUBLIC_BLOCKCHAIN_TESTNET";

        // Create a new wallet
        var wallet = new Wallet();
        System.out.println(String.format("PK: %s, Address: %s", wallet.getPrivateKey(), wallet.getAddress()));

        // Compose a transaction with nonce = 1
        var tx = new Tx(wallet.Address, 1);
        tx.ActionFee = 0.01m; // Set action fee.
        tx.AddTransferChxAction("CHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx", 100); // Transfer 100 CHX to CHxxx... address.    

        System.out.println(tx.toJson(true));
        Console.WriteLine(tx.sign(networkCode, wallet.getPrivateKey()).toJson(false));        
    }    
}
```
