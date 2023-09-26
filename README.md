# Minting NFTs in the UZH-Cardano-Network

This guide provides a step-by-step walkthrough on minting non-fungible tokens (NFTs) within our private Cardano network, known as UZH-Cardano-Network.

### Understanding Native Tokens and Assets

Cardano's Blockchain uniquely enables users to create, manage, and delete custom tokens or 'assets' natively. Here, 'native' implies that besides transacting in Cardano's official currency, ada, users can seamlessly interact with custom assets without relying on smart contracts. While these native assets bear similarities to ada, they also have distinct attributes:

- **Amount/Value**: Specifies the total available.
- **Name**: Descriptive label.
- **Unique PolicyID**: Since asset names aren't unique and can be replicated, each Cardano NFT is distinguished by a unique policyID. This ID arises from a policy script which outlines attributes like the entities allowed to mint tokens and the timeframes for these operations.

Technically, NFTs mirror native assets. However, for a native asset to be considered an NFT, it must be 'non-fungible', indicating that it should possess unique identifiers or traits. Typically, this means the token's quantity is one.

### Time-Locked Constraints for NFTs

Considering the potential trade and sale of NFTs, they must adhere to stringent policies. Often, an asset's value is gauged by its artificial scarcity, which can be controlled using multi-signature scripts. In this guide, we'll implement these constraints:

1. Only a specified signature can mint or burn the NFT.
2. This signature remains valid for 10,000 slots, offering flexibility should any issue arise.

### Our NFT's Reference Image

Our NFT will link to an image ([ipfs://QmRhTTbUrPYEw3mJGGhQqQST9k86v1DPBiTTWJGKDJsVFw](ipfs://QmRhTTbUrPYEw3mJGGhQqQST9k86v1DPBiTTWJGKDJsVFw)) stored on the InterPlanetary File System (IPFS), a decentralized peer-to-peer network for data storage and sharing.
To view the image, access it through the [pinata gateway](https://gateway.pinata.cloud/ipfs/QmRhTTbUrPYEw3mJGGhQqQST9k86v1DPBiTTWJGKDJsVFw).

# 1. Initiating the Process

Start by running a Cardano node and connecting to the UZH-Cardano network. For a comprehensive guide on setting up a Cardano node in the UZH-Cardano network, refer to our [UZH Gitlab repository](https://gitlab.uzh.ch/mostafa.chegenizadeh/uzh-cardano-network) or our [GitHub repository](https://github.com/mostafachegeni/UZH-Cardano-Network).

# 2. Set up a new working directory
It is crucial to organize our files efficiently. Let's begin by creating a new working directory named nft. This will serve as our workspace for all tasks related to this module. Upon executing these commands, you'll have established 'nft' as your current working directory, ensuring all our subsequent activities are neatly contained within this folder. Follow the commands below:
```
mkdir nft
cd nft/
```


# 3. Structuring Important Values
It is essential to make our workflow as seamless as possible. We'll set vital values in variables that are easily readable, ensuring clarity and efficiency throughout our exercise. Notably, the token name should be represented in hexadecimal format. Upon execution, you've assigned the necessary values, including the token name in its hexadecimal representation, ready for the subsequent steps in our process. Follow the commands below:
```
realtokenname="NFT1"
tokenname=$(echo -n $realtokenname | xxd -b -ps -c 80 | tr -d '\n')
tokenamount="1"
ipfs_hash="QmRhTTbUrPYEw3mJGGhQqQST9k86v1DPBiTTWJGKDJsVFw"
```


# 4. Generating Payment Keys and Payment Address
The next pivotal step involves generating the necessary keys and addresses. These are the foundational elements that will enable our token transactions:
```
# Generate the keys
cardano-cli address key-gen --verification-key-file payment.vkey --signing-key-file payment.skey

# Build the address:
cardano-cli address build --payment-verification-key-file payment.vkey --out-file payment.addr --testnet-magic 2023
address=$(cat payment.addr)
```

# 5. Receiving Funds
```
# Display your payment address:
cat payment.addr

# This command MUST be executed on the bootstrap node to send 20 ADA to the address you've just generated:
~/UZH-Cardano-Network/scripts/send_ada.sh 20000000 <ADDRESS>
```
Ensure you replace <ADDRESS> with the payment address you previously displayed.


To check if the address has successfully received the funds, use the following command:
```
cardano-cli query utxo --address $address --testnet-magic 2023
```


# 6. Exporting Protocol Parameters
To ensure we are all aligned with the network's current configuration, we'll now export the protocol parameters. This step ensures that we work with the most recent network settings:
```
cardano-cli query protocol-parameters --testnet-magic 2023 --out-file protocol.json
```
By executing the above command, you'll have saved the protocol parameters to a file named protocol.json, which will be referenced in our subsequent steps.


# 7. 




# 8. 




# 9. 






# 10. 






# 11. 


