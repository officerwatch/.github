### officer.watch 
##### *a modern remix of the Berkley Copwatch Database*


## /web
The **web** repo is for the *officer.watch* website. It's a single-page web app that's built on React and written in TypeScript.

It can be configured to be globally accessible, censor-proof & published to IPFS mirror servers. This means that even if the primary website ( officer.watch ) goes down for any reason, it can still be accessed through an IPFS hash and served from any number of other hosts.

There is no reliance on a web server for this website. That's one of the core philophies behind web3.

It serves the following roles:
 - Communicate with in-browser wallet ( eg. MetaMask ) to manage a users's identity
 - Authenticate user identities by talking directly to the blockchain
 - Fetch copwatch database information directly from GraphQL API
 - Host an in-browser data cache so database can be read while offline

 ## /graphql
The **graphql** repo is the GraphQL API. It's built on Node & written in JavaScript.

GraphQL was chosen because it has a great interface for selecting specific sets of data and works very well with the React-based user interface. GraphQL also supports using another data source ( eg. REST ) as a backend source of information. In our use case, JSON-RPC is being queried and relayed behind the scenes. There is also caching done for optimized initial loads of the website.

It serves the following roles:
 - *read/view* operations to fetch objects stored in the blockchain
 - supplies the current state of the data store to users on the website

## /blockchain
The **blockchain** repo is the code that gets published to & lives on the blockchain. It operates as an app that stores and retrieves data objects.

This "smart contract" is written in the Solidity language as is meant to be published to an Ethereum Virtual Machine compatible blockchain. Currently Polygon/MATIC is the target blockchain due to low cost per transactions.

The application is globally accessible from a community of thousands of servers and the data is immutable. So the public data objects are stored in a location that can never be tampered with and never be taken down. Even if the website implodes and the IPFS mirrors all fail, anyone from anywhere can still read the public data with the GraphQL API.

It serves the following roles:
 - Store "objects" of data. Which is basically some small bits of metadata about a particular thing ( officer, incident, picture, document, etc ) and the IPFS hash of the full current version of that thing
 - Maintain a list of access privileged users that are allowed to publish directly to the object store
 - Public access points suited for the GraphQL API to easily fetch the data it needs

## /ipfs
The **ipfs** repo is home to an API that's written in JavaScript and has setup instructions on how to run an IPFS HTTP Gateway & IPFS RPC API.

The purpose of the API is to allow any guest & volunteer the ability to upload multimedia, documents, and submit other information for volunteers to review and publish to the blockchain data store. 

Guest information that's located here is private and not written to the blockchain. It's stored in a secure/temporary holding area, whereas volunteer submissions get written directly to the blockchain and are public.

IPFS is a content-centric decentralized file storage system that allows public information to easily spread to multiple hosts. More information can be found in the developer documentation. Instructions for working with IPFS data mirroring ( or "pinning" ) services are also found in the developer docs.

It serves the following roles:
 - Allow anyone to supply intake information & multimedia for review
 - Places object data from pre-approved users into permanent storage

## /developer
The **developer** repo is for the developer documentation website. It's synced to the Gitbook hosted service. Editing markdown files on Github will trigger a sync to Gitbook and publish the changes to the website. No functional part of the running system resides in this repo. It's strictly for planning purposes only.

## /.github
The **.github** repo is what Github forces people to create to have a README file at the github.com/officerwatch URL. Kinda wish this would be hidden. Please ignore this repo. No functional part of the running system resides in this repo.
