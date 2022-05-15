### officer.watch 
##### *a modern remix of the Berkley Copwatch Database*


## /web
The **web** repo is for the *officer.watch* website. It's a single-page web app that's built with React/JavaScript.

It serves the following roles:
 - Communicate with in-browser wallet ( eg. MetaMask ) to manage a users's identity
 - Authenticate user identities by talking directly to the blockchain
 - Fetch copwatch database information directly from GraphQL API
 - Configured to be globally accessible, censor-proof & published to IPFS 
 - Allow anyone to supply intake information & multimedia for review

 ## /api
The **api** repo is the GraphQL data API. It's built with Node/JavaScript.

It's primarily purpose is for *read/view* operations to fetch copwatch data from the blockchain. In the future, it can be setup for *write/update* operations to the blockchain on behalf of a website user or from a generic "admin" user.

GraphQL was chosen because it has a great interface for selecting specific sets of data and works very well with the React-based user interface. GraphQL also supports using another data source ( eg. REST ) as a backend source of information. In our use case, JSON-RPC is being queried and relayed behind the scenes. 

## /blockchain
The **blockchain** repo is the code that gets published to the blockchain, and operates as an app that stores and retrieves data.

This "smart contract" is written in the Solidity language as is meant to be published to an Ethereum Virtual Machine compatible blockchain. Currently Polygon/MATIC is the target blockchain due to low cost per transactions.

The application is globally accessible from a community of thousands of servers and the data is immutable. So the public copwatch data that is stored in a location that can never be tampered with and never be taken down. Even if the website implodes and the IPFS mirrors all fail, anyone from anywhere can still read the public data.

## /intake
The **intake** repo is home to an HTTP API that's written in Go.

The purpose of the API is to allow anyone the ability to upload multimedia, documents, and submit other information for volunteers to review and publish to the copwatch database. 

The data that's stored here is private and not written to the blockchain. It's stored locally in a Redis database on the same server as the Go app.

## /ops
The **ops** repo is for project contributors to version control the data model planning and other operations/planning related aspects of information management.

No functional part of the running system resides in this repo. It's strictly for planning purposes only.
