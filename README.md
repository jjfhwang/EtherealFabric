# EtherealFabric: Decentralized DAG Consensus Prototypes

EtherealFabric is a Python-based research and development project focused on exploring the frontiers of decentralized consensus mechanisms. It prototypes a novel approach to distributed ledger technology, leveraging Directed Acyclic Graph (DAG) structures to achieve high throughput and scalability. The core innovation lies in its integration of sharded, zero-knowledge smart contracts, enabled through verifiable random functions (VRFs) and homomorphic encryption, aiming for enhanced privacy and efficiency in decentralized applications.

This repository contains early-stage prototypes and experimental code demonstrating the feasibility of the proposed concepts. It is designed for researchers, developers, and enthusiasts interested in exploring advanced consensus algorithms, privacy-preserving technologies, and the future of decentralized systems. The project aims to address the limitations of traditional blockchain architectures by offering a more flexible and scalable alternative, particularly for applications requiring sophisticated smart contract functionality and data confidentiality.

EtherealFabric seeks to provide a framework for building decentralized applications that can handle a large volume of transactions while maintaining user privacy. It explores the potential of combining DAG-based consensus with cryptographic techniques to create a system resistant to censorship and collusion. The project is open-source and welcomes contributions from the community to further develop and refine the proposed architecture. This repository serves as a platform for experimentation, evaluation, and iteration on novel concepts in the field of decentralized technologies.

## Key Features

*   **DAG-based Consensus:** Implements a custom DAG consensus algorithm, allowing for parallel transaction processing and improved throughput compared to traditional blockchain systems. The algorithm includes mechanisms for conflict resolution and finality determination based on weighted node confirmations.
*   **Sharded Smart Contracts:** Employs a sharding strategy to distribute smart contract execution across multiple nodes, increasing scalability and reducing computational overhead. Shard assignment is dynamically managed using a decentralized mechanism.
*   **Zero-Knowledge Smart Contracts:** Integrates zero-knowledge proofs (ZK-SNARKs) to enable private and verifiable smart contract execution. This allows users to execute contracts without revealing sensitive data on the public ledger.
*   **Verifiable Random Functions (VRFs):** Utilizes VRFs for secure and unpredictable leader election in the DAG consensus process and for shard assignment. VRFs ensure fairness and prevent malicious actors from manipulating the system.
*   **Homomorphic Encryption:** Leverages homomorphic encryption (specifically, partially homomorphic encryption schemes like Paillier) to allow computations on encrypted data within smart contracts. This provides an additional layer of privacy for sensitive information.
*   **Modular Architecture:** Designed with a modular architecture to facilitate experimentation with different consensus algorithms, cryptographic primitives, and sharding strategies. This allows for easy swapping of components and rapid prototyping of new features.
*   **Proof-of-Concept Smart Contract Engine:** Includes a basic smart contract engine capable of executing simple contracts written in a custom domain-specific language (DSL). This engine demonstrates the integration of zero-knowledge proofs and homomorphic encryption within the smart contract execution environment.

## Technology Stack

*   **Python:** The primary programming language used for implementing the consensus algorithm, smart contract engine, and cryptographic primitives.
*   **Cryptographic Libraries (e.g., PyCryptodome, Charm-Crypto):** Used for implementing various cryptographic operations, including VRFs, zero-knowledge proofs, and homomorphic encryption. PyCryptodome provides general cryptographic functionality, while Charm-Crypto offers support for advanced cryptographic schemes.
*   **NetworkX:** Used for representing and manipulating the DAG structure. NetworkX provides efficient algorithms for graph traversal and analysis.
*   **Serialization Libraries (e.g., Pickle, JSON):** Used for serializing and deserializing data structures for network communication and storage.
*   **Testing Frameworks (e.g., pytest):** Used for writing and running unit tests to ensure the correctness and robustness of the codebase.
*   **asyncio:** Python's built-in asynchronous I/O library is used for handling concurrent network operations and improving performance.

## Installation

1.  Clone the repository:
    git clone https://github.com/jjfhwang/EtherealFabric.git
    cd EtherealFabric

2.  Create a virtual environment:
    python3 -m venv venv
    source venv/bin/activate

3.  Install the required dependencies:
    pip install -r requirements.txt

4. If you encounter issues with specific crypto libraries, ensure you have the necessary system dependencies installed (e.g., libgmp-dev for Charm-Crypto):
    sudo apt-get update
    sudo apt-get install libgmp-dev

## Configuration

The EtherealFabric prototypes utilize environment variables for configuration. Create a `.env` file in the root directory of the project and define the following variables:

*   `NODE_ID`: A unique identifier for each node in the network (e.g., 1, 2, 3).
*   `PORT`: The port number the node will listen on (e.g., 5000).
*   `BOOTSTRAP_NODE_IP`: The IP address of a bootstrap node in the network (used for initial peer discovery). Leave blank for the first node.
*   `BOOTSTRAP_NODE_PORT`: The port number of the bootstrap node.
*   `PRIVATE_KEY`: The node's private key (used for signing transactions and messages). If not provided, a new key will be generated. For testing, pre-generated keys are acceptable.
*   `VRF_SECRET_KEY`: Secret Key needed for the VRF. Must be consistent for all nodes.

Example `.env` file:
NODE_ID=1
PORT=5000
BOOTSTRAP_NODE_IP=
BOOTSTRAP_NODE_PORT=
PRIVATE_KEY=your_private_key
VRF_SECRET_KEY=some_secret_key

## Usage

To run a node:
python main.py

The `main.py` script initializes a node, connects to the network (if a bootstrap node is specified), and starts listening for incoming transactions and messages. You can then interact with the node using its API (currently under development, but basic functions like submitting transactions will be available).

Example: Submitting a transaction (simplified for demonstration, actual API will be more robust):
python submit_transaction.py --recipient <recipient_address> --amount <amount> --private_key <your_private_key>

(submit_transaction.py would be a separate script, not included directly in the EtherealFabric download, for submitting transactions.)

Refer to the inline documentation within the code for more detailed information on the available functions and APIs. Note that this is a prototype, and the API is subject to change.

## Contributing

We welcome contributions to EtherealFabric! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear and concise commit messages.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure your code is well-tested and documented.
6.  Follow the existing code style and conventions.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/jjfhwang/EtherealFabric/blob/main/LICENSE) file for details.

## Acknowledgements

This project is inspired by the work of numerous researchers and developers in the fields of distributed systems, cryptography, and blockchain technology. We would like to thank the open-source community for their invaluable contributions and resources. We also acknowledge the foundational work on DAG consensus mechanisms and privacy-preserving technologies that have paved the way for this project.