# Mood NFT

This project showcases a novel approach to Non-Fungible Tokens (NFTs) by implementing a dynamic NFT that allows its visual representation to change based on user interaction. The MoodNft contract enables the owner of a token to "flip" its mood between a happy 😊 and a sad 😔 face.

**Key Features & Technical Highlights:**

**Dynamic On-Chain Visuals:** Unlike static NFTs, the artwork of each Mood NFT can be altered post-minting by the token owner. This demonstrates a powerful concept of NFTs evolving based on interaction, rather than being fixed at creation.
100% On-Chain SVG Rendering: The core innovation lies in generating the NFT's SVG (Scalable Vector Graphics) image directly within Solidity. The contract stores the raw SVG definitions and dynamically constructs the image data.
Base64 Encoding & Data URIs: The SVG content is Base64 encoded on-chain, then embedded into a Base64 encoded JSON metadata string, which is finally returned as a data URI from the tokenURI function. This eliminates reliance on centralized servers for image hosting.

**Decentralized Storage (Conceptual):** By generating the SVG and metadata dynamically on-chain and returning it as a data URI, the NFT's "artwork" is inherently part of the blockchain's state, or fetched directly from it, which aligns with principles of decentralization and censorship resistance. While IPFS is a separate layer, the design minimizes off-chain dependencies for the art itself.
ERC721 Standard Compliant: The MoodNft contract adheres to the ERC721 token standard, ensuring compatibility with NFT marketplaces and wallets.
**Built with Foundry:** The project is developed using Foundry, leveraging Forge for robust testing and Cast for command-line interaction with the smart contract.

## Contract Overview:
The primary contract, MoodNft.sol, includes:

**constructor(string memory happySvg_, string memory sadSvg_):** Initializes the contract with the raw SVG strings for the happy and sad moods.
**mintNft():** Allows users to mint a new Mood NFT, initially set to a happy mood.
**flipMood(uint256 tokenId):** A function callable by the token owner to switch the mood of a specific NFT.
**tokenURI(uint256 tokenId):** An overridden ERC721 function that dynamically generates the full Base64 encoded JSON data URI for the NFT, incorporating its current mood's SVG.
**Usage & Deployment:**
**Local Development:** Interact with the contract using Anvil for a local blockchain environment.
**Testnet Deployment:** The contract can be deployed to public testnets like Sepolia to demonstrate its functionality in a live, decentralized environment.
This project serves as a strong example of creating truly dynamic and self-contained NFTs entirely on the Ethereum Virtual Machine (EVM).