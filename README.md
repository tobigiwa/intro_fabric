# Hyperledger Fabric

If you're here you must be coming from the pre-sequel to this article, if not, here it is. This one would be a short overview of the workings of Hyperledger Fabric (HF) and as developers, we know where to find all to it, the [documentation](https://hyperledger-fabric.readthedocs.io/en/release-2.5/whatis.html#), and the one for Hyperledger Fabric is solid. As we know, HF is;

> "[Hyperledger Fabric is an open source enterprise-grade permissioned distributed ledger technology (DLT) platform, designed for use in enterprise contexts, that delivers some key differentiating capabilities over other popular distributed ledger or blockchain platforms](https://hyperledger-fabric.readthedocs.io/en/release-2.5/whatis.html#hyperledger-fabric)".

I'll strongly recommend you use the docs at first and especially the [Key concept section](https://hyperledger-fabric.readthedocs.io/en/release-2.5/key_concepts.html), it explains enough to get a good overview of the architecture of the technology, forget using a book.

So, at the base unit, a Fabric network consists of a **Channel**, or Channels in a bigger scope. This channels is where the _privacy and permission_ comes in, it like a room or roundtable where transaction and communication happens, now the creation of a channel is a **channel configuration**, sort of like a policy that defines the rules and guides of the channel from a _configtx.yaml_ created by a _configtxgen tool_. 

**Organizations** are the corporate entity that wants to transact on a channel, each organization is expected to come with at least a **Peer node**, this peer node is a fundamental component of the network beacause this is where the chaincode lives (a moniker for what HF calls it smartcontract). This chaincode defines the rules/contract between different organizations in executable code, this is the code that access the ledger. 

The **Ledger** which is also housed on the peer node consist of the **Blockchain** and a **World State**, allow me explain. The Blockchain is the blockchain, the immutable, append-only log of all the transaction in the network. The world state on the other hand is a database that stores the current value of the asset on a blockchain, why is that???, it is because mosts programs(chaincode/smartcontract) usually require the current value of an object; it would be cumbersome to traverse the entire blockchain to calculate an object’s current value – you just get it directly from the world state, period. Currently now the Fabric network supports only LevelDB and CouchDB, a key-value document database(as I understands it), so this database is frequently changing. To add, if you sum up all the history of the asset in the blockchain at an instant of time, you'll get the valu in the world state at that instance, I think I've nailed that enough.

Still on the peer nodes, not all peer nodes are the same. There are different types of peer nodes with different roles in the network:

> Endorser peer: Validates transaction (check certificate details and roles) and executes chaincode.

> Anchor peer :  enable cross-organization communication among peer nodes using the Hyperledger Fabric gossip protocol

> Orderer peer : responsible for establishing the correct order of all transactions

Am sure you're getting a feeling there more to this, and yes there is, please check out the docs and maybe Youtube. One thing I want to add is the **Fabric Gateway Service** on the Peer that exposes API that the clients (your backend) can use to interact with the network.

 The last thing I will like to mention is the **MSP (Member Service Provider)** - everything that interacts with a blockchain network, including peers, applications, admins, and orderers, acquires their organizational identity from their digital certificate and their Membership Service Provider (MSP) definition. The MSP is like the one who says "who is who", "where from" and "what role they perform".

 So, what have we mentioned here; Channel, Organization, Peer Nodes (Endorser, Anchor, Orderer), Chaincode, Fabric Gateway, the Ledger (blockchain and world state) and the MSP. Really with this few going through the docs would be a breeze. THE END.

 In my next article, I'll be introducing the smartcontract side of the network (chaincode), I'll explain the two API library (lower-level and high-level) in Go. I should mention that there 

