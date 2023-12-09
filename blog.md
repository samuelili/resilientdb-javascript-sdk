# Introduction to ResilientDB TypeScript SDK: Building Robust Applications

The digital era demands robust solutions that can handle data with precision, security, and flexibility. Blockchain technology is championing this revolution, and at the heart of many innovative applications is ResilientDB, a versatile distributed ledger that offers both trust and transparency.

In this depth look, we will explore the ResilientDB TypeScript SDK, an essential toolkit for developers seeking to leverage the ResilientDB platform in their JavaScript and TypeScript applications. Through the integration of GraphQL, the SDK simplifies interactions with the ResilientDB server, enabling easy queries and mutations to manage transactions effectively.

## What Is ResilientDB?

ResilientDB is a distributed ledger infrastructure that emphasizes resilience, scalability, and decentralized control. It allows applications to perform transactions in a distributed environment with trust and transparency being paramount.

## NPM Package: `resilientdb-javascript-sdk`

Before diving deep into the codebase, let's address how to get the SDK into your project. The `resilientdb-javascript-sdk` is readily available on the NPM registry and can be included in your project with ease.

### Installation

To install the SDK, run the following command in your project directory:

```sh
npm install resilientdb-javascript-sdk
```

## Introducing the SDK

The SDK comes with three main modules that form its core functionality. Each plays a significant role in ensuring a streamlined interface for communicating with the ResilientDB server.

### Clients

The `FetchClient` and `AxiosClient` are two interchangeable network clients that ResilientDB utilizes to make HTTP requests to the ResilientDB server.

#### FetchClient (`FetchClient.ts`)

A lightweight client using the Fetch API. It’s optimal for environments where size and simplicity are key.

Example of initializing a `FetchClient`:

```typescript
import { ResilientDB, FetchClient } from 'resilientdb-javascript-sdk';

const fetchClient = new FetchClient();
```

#### AxiosClient (`AxiosClient.ts`)

A feature-rich client based on `axios`. This client is suited for those who may need interceptors, progress indicators, or other advanced features provided by `axios`.

Example of initializing an `AxiosClient`:

```typescript
import { ResilientDB, AxiosClient } from 'resilientdb-javascript-sdk';

const axiosClient = new AxiosClient();
```

### ResilientDB Client (`ResilientDB.ts`)

The SDK’s main class provides a user-friendly interface to the ResilientDB server's GraphQL API. It includes methods for retrieving, filtering, and posting transactions, as well as generating cryptographic key pairs.

### Core Types (`types.ts`)

Defines the interfaces and types used throughout the SDK, ensuring type safety and developer experience.

## ResilientDB Client Methods

Here's a detailed look at each method provided by the `ResilientDB` client.

### Transaction Retrieval Methods

| Method                       | Input Parameters                            | Output                                        | Description                                                        |
|------------------------------|---------------------------------------------|-----------------------------------------------|--------------------------------------------------------------------|
| `getTransaction`             | `requestId: string`                         | `Promise<RetrieveTransaction>`                | Retrieves a single transaction by its unique ID.                    |
| `getAllTransactions`         | -                                           | `Promise<RetrieveTransaction[]>`              | Fetches all transactions.                                           |
| `getFilteredTransactions`    | `filter?: FilterKeys`                       | `Promise<RetrieveTransaction[]>`              | Retrieves transactions that match the given filtering criteria.     |

- **FilterKeys**: A type that includes optional fields for filtering transactions by `ownerPublicKey` and `recipientPublicKey`.

### Transaction Mutation Methods

| Method                       | Input Parameters                            | Output                                        | Description                                                        |
|------------------------------|---------------------------------------------|-----------------------------------------------|--------------------------------------------------------------------|
| `postTransaction`            | `transaction: PrepareAsset`                 | `Promise<CommitTransaction>`                  | Posts a new transaction to the ledger.                              |
| `updateTransaction`          | `transaction: UpdateAsset`                  | `Promise<RetrieveTransaction>`                | Updates an existing transaction.                                    |
| `updateMultipleTransaction`  | `transactions: UpdateAsset[]`               | `Promise<RetrieveTransaction[]>`              | Updates multiple transactions at once.                              |

- **PrepareAsset**: A type representing the necessary information to prepare a transaction for posting.
- **UpdateAsset**: A type used for detailing the specifications required to update a transaction.
- **CommitTransaction**: Represents the output of posting a new transaction, which includes, at minimum, the `id` of the committed transaction.

### Key Generation Method

| Method                      | Input Parameters                            | Output                                    | Description                                                        |
|-----------------------------|---------------------------------------------|-------------------------------------------|--------------------------------------------------------------------|
| `static generateKeys()`     | -                                           | `{ publicKey: string; privateKey: string}`| Generates a pair of public and private keys for signing transactions.|


## SDK Demo Application

Included within the SDK repository is a demo React application that showcases the SDK's capabilities. The app allows users to filter transactions, post new transactions, and explore the core features of the ResilientDB TypeScript SDK.

## Real-World Value and Implications

By simplifying the integration and interaction with the ResilientDB server, the SDK opens the door to a plethora of applications. Whether you're developing a finance app that requires ledger capabilities or seeking the immutability of blockchain for asset tracking, the ResilientDB TypeScript SDK is a capable starting point.

The versatility in choosing between the `FetchClient` and the `AxiosClient` ensures developers have the liberty to pick a client that best suits their specific needs, whether they prioritize speed and minimalism or extensive features.

## Conclusion

The ResilientDB TypeScript SDK stands as a testament to the possibilities when modern web technologies meet blockchain principles. Through its approachable interface and adaptable architecture, the SDK demonstrates how applications can be built with resilience at their core, ready to scale and secure transactions across a distributed network.

Whether you're an experienced blockchain developer or a newcomer to distributed ledger technology, the SDK provides the necessary tools to interface with the ResilientDB platform with confidence and ease.