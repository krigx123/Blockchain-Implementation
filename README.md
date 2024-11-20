
# Blockchain Implementation

This project is a basic blockchain implementation with a Flask-powered API, allowing users to interact with the blockchain. It supports adding transactions, mining blocks, and viewing the full blockchain.


## Features

1. **Blockchain Core**:

- Implements essential blockchain concepts: blocks, transactions, proof of work, and hashing.
- Includes a genesis block as the starting point of the chain.

2. **Proof of Work**:

- Utilizes a simple proof-of-work algorithm to secure the blockchain.
- Requires the proof to generate a hash starting with four leading zeroes.

3. **Transactions**:

- Allows users to create transactions by specifying sender, recipient, and amount.

4. **API Endpoints**:

- `/mine`: Mines a new block using the proof-of-work algorithm and adds it to the chain.
- `/transactions/new`: Accepts new transactions.
- `/chain`: Returns the current state of the blockchain.

5. **Flask Framework**:

- Provides RESTful endpoints for interaction.


## Usage

### Running the Application

- Save the code to a file, e.g., `blockchain.py`.
- Start the server:
```bash
python blockchain.py
```
- The server will run on `http://0.0.0.0:5001`.


## API Reference

1. **Mine a Block**
- Endpoint: `/mine`
- Method: `GET`
- Description: Mines a new block and adds it to the chain.
- Response: 
```json
{
    "message": "New Block Forged",
    "index": 2,
    "transactions": [],
    "proof": 35293,
    "previous_hash": "abc123..."
}
```

2. **Create a Transaction**
- Endpoint: `/transactions/new`
- Method: `POST`
- Payload:
```json
{
    "sender": "address1",
    "recipient": "address2",
    "amount": 50
}
```
- Response: 
```json
{
    "message": "Transaction will be added to Block 2"
}
```

3. **View the Blockchain**
- Endpoint: `/chain`
- Method: `GET`
- Description: Fetches the entire blockchain.
- Response: 
```json
{
    "chain": [...],
    "length": 2
}
```
## Code Overview

### `Blockchain` Class
- `new_block(proof, previous_hash)`: Adds a new block.
- `new_transaction(sender, recipient, amount)`: Adds a new transaction.
- `proof_of_work(last_proof)`: Generates proof of work.
- `valid_proof(last_proof, proof)`: Validates proof of work.
- `hash(block)`: Creates a hash for a block.

### Flask API
- `/mine`: Mines a new block.
- `/transactions/new`: Adds a transaction.
- `/chain`: Returns the blockchain.
## Example Workflow

- Add a transaction using `/transactions/new`.
- Mine a block using `/mine`.
- View the updated blockchain using `/chain`.