# Simple Python Blockchain

This is a simple blockchain implementation in Python, using Flask for the web interface. The application allows you to create a blockchain, mine new blocks, create transactions, register nodes, and resolve conflicts using a consensus algorithm.

## Features

- **Blockchain Class**:
  - `__init__`: Initializes the blockchain with an empty chain and current transactions list. Creates the genesis block.
  - `new_block`: Creates a new block in the blockchain.
  - `hash`: Creates a SHA-256 hash of a block.
  - `last_block`: Returns the last block in the chain.
  - `new_transaction`: Creates a new transaction to be added to the next mined block.
  - `proof_of_work`: Implements a simple proof of work algorithm.
  - `valid_proof`: Validates the proof by checking if the hash contains leading 4 zeroes.
  - `register_node`: Registers a new node by parsing its address and adding it to the set of nodes.
  - `valid_chain`: Determines if a given blockchain is valid.
  - `resolve_conflicts`: Implements the consensus algorithm by checking and validating chains from all registered nodes.

- **Flask Application**:
  - `/mine` endpoint: Mines a new block by running the proof of work algorithm, rewards the miner, and adds the new block to the chain.
  - `/transactions/new` endpoint: Creates a new transaction and adds it to the list of current transactions.
  - `/chain` endpoint: Returns the full blockchain.
  - `/nodes/register` endpoint: Registers new nodes with the blockchain network.
  - `/nodes/resolve` endpoint: Resolves conflicts by replacing the current chain with the longest valid chain.

## Installation

1. **Clone the repository**:
    ```sh
    git clone https://github.com/alessandro-zanella/simple_python_blockchain_v1.git
    cd simple_python_blockchain_v1
    ```

2. **Install dependencies**:
    ```sh
    pip install -r requirements.txt
    ```

## Usage

1. **Run the application**:
    ```sh
    python blockchain.py --port 6969
    ```
On a second terminal (2nd Node e.g port 7474)
    ```sh
    python blockchain.py --port 7676
    ```

##  Dublicate all these commands with a different port (e.g. 7676) To let nodes communicate 

2. **Endpoints**:

    - **Mine a new block**:
        ```sh
        GET /mine
        ```
        Example:
        ```sh
        curl -X GET http://127.0.0.1:6969/mine
        ```

    - **Create a new transaction**:
        ```sh
        POST /transactions/new
        ```
        Example:
        ```sh
        curl -X POST -H "Content-Type: application/json" -d '{"sender": "address1", "recipient": "address2", "amount": 5}' http://127.0.0.1:6969/transactions/new
        ```

    - **View the full blockchain**:
        ```sh
        GET /chain
        ```
        Example:
        ```sh
        curl -X GET http://127.0.0.1:6969/chain
        ```

    - **Register a new node**:
        ```sh
        POST /nodes/register
        ```
        Example:
        ```sh
        curl -X POST -H "Content-Type: application/json" -d '{"nodes": ["http://127.0.0.1:7676"]}' http://127.0.0.1:6969/nodes/register
        ```

    - **Resolve conflicts**:
        ```sh
        GET /nodes/resolve
        ```
        Example:
        ```sh
        curl -X GET http://127.0.0.1:6969/nodes/resolve
        ```

## Methods

### Blockchain Class

- **[__init__](http://_vscodecontentref_/0)**:
    Initializes the blockchain with an empty chain and current transactions list. Creates the genesis block.

- **`new_block(proof, previous_hash=None)`**:
    Creates a new block in the blockchain.
    - [proof](http://_vscodecontentref_/1): The proof given by the Proof of Work algorithm.
    - [previous_hash](http://_vscodecontentref_/2): (Optional) Hash of the previous block.

- **[hash(block)](http://_vscodecontentref_/3)**:
    Creates a SHA-256 hash of a block.
    - [block](http://_vscodecontentref_/4): The block to hash.

- **[last_block](http://_vscodecontentref_/5)**:
    Returns the last block in the chain.

- **`new_transaction(sender, recipient, amount)`**:
    Creates a new transaction to be added to the next mined block.
    - [sender](http://_vscodecontentref_/6): Address of the sender.
    - [recipient](http://_vscodecontentref_/7): Address of the recipient.
    - [amount](http://_vscodecontentref_/8): Amount of the transaction.

- **[proof_of_work(last_proof)](http://_vscodecontentref_/9)**:
    Implements a simple proof of work algorithm.
    - [last_proof](http://_vscodecontentref_/10): The previous proof.

- **`valid_proof(last_proof, proof)`**:
    Validates the proof by checking if the hash contains leading 4 zeroes.
    - [last_proof](http://_vscodecontentref_/11): The previous proof.
    - [proof](http://_vscodecontentref_/12): The current proof.

- **[register_node(address)](http://_vscodecontentref_/13)**:
    Registers a new node by parsing its address and adding it to the set of nodes.
    - [address](http://_vscodecontentref_/14): Address of the node.

- **[valid_chain(chain)](http://_vscodecontentref_/15)**:
    Determines if a given blockchain is valid.
    - [chain](http://_vscodecontentref_/16): The blockchain to validate.

- **[resolve_conflicts()](http://_vscodecontentref_/17)**:
    Implements the consensus algorithm by checking and validating chains from all registered nodes.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- This project is a direct result of studying [Blockchain Demo](https://github.com/dvf/blockchain) by Daniel van Flymen.