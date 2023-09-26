### Minting NFTs in the UZH-Cardano-Network

This guide provides a step-by-step walkthrough on minting non-fungible tokens (NFTs) within our private Cardano network, known as UZH-Cardano-Network.

#### Understanding Native Tokens and Assets

Cardano's Blockchain uniquely enables users to create, manage, and delete custom tokens or 'assets' natively. Here, 'native' implies that besides transacting in Cardano's official currency, ada, users can seamlessly interact with custom assets without relying on smart contracts. While these native assets bear similarities to ada, they also have distinct attributes:

- **Amount/Value**: Specifies the total available.
- **Name**: Descriptive label.
- **Unique PolicyID**: Since asset names aren't unique and can be replicated, each Cardano NFT is distinguished by a unique policyID. This ID arises from a policy script which outlines attributes like the entities allowed to mint tokens and the timeframes for these operations.

Technically, NFTs mirror native assets. However, for a native asset to be considered an NFT, it must be 'non-fungible', indicating that it should possess unique identifiers or traits. Typically, this means the token's quantity is one.

#### Time-Locked Constraints for NFTs

Considering the potential trade and sale of NFTs, they must adhere to stringent policies. Often, an asset's value is gauged by its artificial scarcity, which can be controlled using multi-signature scripts. In this guide, we'll implement these constraints:

1. Only a specified signature can mint or burn the NFT.
2. This signature remains valid for 10,000 slots, offering flexibility should any issue arise.

#### Our NFT's Reference Image

Our NFT will link to an image ([ipfs://QmRhTTbUrPYEw3mJGGhQqQST9k86v1DPBiTTWJGKDJsVFw](ipfs://QmRhTTbUrPYEw3mJGGhQqQST9k86v1DPBiTTWJGKDJsVFw)) stored on the InterPlanetary File System (IPFS), a decentralized peer-to-peer network for data storage and sharing.

To view the image, access it through the pinata gateway:
[https://gateway.pinata.cloud/ipfs/QmRhTTbUrPYEw3mJGGhQqQST9k86v1DPBiTTWJGKDJsVFw](https://gateway.pinata.cloud/ipfs/QmRhTTbUrPYEw3mJGGhQqQST9k86v1DPBiTTWJGKDJsVFw)

#### Initiating the Process

Start by running a Cardano node and connecting to the UZH-Cardano network. For a comprehensive guide on setting up a Cardano node in the UZH-Cardano network, refer to our UZH Gitlab repository:
[https://gitlab.uzh.ch/mostafa.chegenizadeh/uzh-cardano-network](https://gitlab.uzh.ch/mostafa.chegenizadeh/uzh-cardano-network)
