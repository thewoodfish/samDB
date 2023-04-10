## SamaritanDB - A distributed decentralised identity-database
SamaritanDB is an identity database which stores in particular, defining and describing user data.
The database is an high-speed in-memory distributed key-value database. It was created to help solve the problem of centralization and control of data and its access points. 
SamaritanDB gives power to the app owners and provides them with a censorship-resistant, decentralized and distributed key-value store. This prevents any storage or cloud provider from waking up tomorrow and cutting the app off the internet because they had a nightmare. 
The database does not stop there, it also protects the users of the apps and gives them the power to control the access to the data stored about them by the apps! Sick! 
## Technologies
SamaritanDB is built with/on three major technologies:
- IPFS 
- ink! (a Rust embedded domain-specific language (eDSL) for writing smart contracts)
- The Rust Language
## Commands supported
Please note that the commands below would be abstracted away by client libraries and UIs, these are the bare commands at the TCP level:
- <b>Command:</b> `NEW::<sam|app>::<Password>`<br>
<b>Returns:</b> `DID` of the format `did:sam:root:<45 random alphanumeric characters>` for Samaritans(See footnote), or `did:sam:apps:<45 random alphanumeric characters>` for applications.<br>
<b>Function:</b> This creates an account onchain for the app or the samaritan. This is necessary before any operation can be made on the database because everything about the SamDB is `DID` oriented. All data stored about an app or a samaritan is associated with a decentralized identifier implicitly.
- <b>Command:</b> `INIT::<did:sam:apps:<45 random alphanumeric characters>>::<Password>`<br>
<b>Function:</b> A SamaritanDB can be spun up on any machine on earth, thanks to IPFS. This command authenticates the app onchain and when its recognized, its most recent and important files are quickly retrived from the network to create a weak locality of reference.
- <b>Command:</b> `INSERT::<did:sam:apps:<45 random alphanumeric characters>>::<Key>::<Value>::[did:sam:root:<45 random alphanumeric characters>]`<br>
<b>Returns:</b> The `key`, the `value` inserted and the previous `value` stored, if any.</br>
<b>Function:</b> This inserts a key-value pair into the database. The last argument is optional. If specified, it demonstrates that the data stored is in relations to a samaritan.
- <b>Command:</b> `GET::<did:sam:apps:<45 random alphanumeric characters>>::<Key>::[did:sam:root:<45 random alphanumeric characters>]`</br>
<b>Returns:</b> The `key` and its `value`.</br>
<b>Function:</b> This returns the value of the key specified in the database. The last argument is optional. If specified, it helps retreive data the samaritan owns, that is stored by the app.
- <b>Command:</b> `DEL::<did:sam:apps:<45 random alphanumeric characters>>::<Key>::[did:sam:root:<45 random alphanumeric characters>]`</br>
<b>Returns:</b> The `key` and its `value`.</br>
<b>Function:</b> This deletes the value of the key specified in the database. The last argument is optional. If specified, it helps delete data the samaritan owns, that is stored by the app.
- <b>Command:</b> `REVOKE::<did:sam:root:<45 random alphanumeric characters>>::<did:sam:apps:<45 random alphanumeric characters>>`</br>
<b>Returns:</b> The `DID` of the app which access was revoked.</br>
<b>Function:</b> Revokes the access of the specified app to the data associated with a samaritan.
- <b>Command:</b> `UNREVOKE::<did:sam:root:<45 random alphanumeric characters>>::<did:sam:apps:<45 random alphanumeric characters>>`</br>
<b>Returns:</b> The `DID` of the app which access was unrevoked.</br>
<b>Function:</b> Unrevokes the access of the specified app to the data associated with a samaritan.
- <b>Command:</b> `AUTH::<did:sam:root:<45 random alphanumeric characters>>::<Password>`</br>
<b>Function:</b> Authenticates a samaritan and immediately fetches the data the application stores about the Samaritan.
- <b>Command:</b> `GETALL::<did:sam:apps:<45 random alphanumeric characters>>::[<did:sam:root:<45 random alphanumeric characters>>]`</br>
<b>Returns:</b> All data stored by an application. If a samaritans `DID` is present, all data the application stored about a samaritan is returned.</br>
<b>Function:</b> Fetches all data an application stores about itself or about a samaritan.

## How does the database work?
First, because the database persists its data on nodes EXPOSED by IPFS and stores the currently used data in memory, it is required to download IPFS on the machine running the database. Also, the IPFS daemon must be started to help advertise and push data to other nodes that would be needing it, otherwise the data is just pushed locally waiting for the deamon to come online.
It is also mandatory to be connected to the internet for quering the smart contract node and submitting transactions. 
Data is stored in-memory by the database to ensure speed. There are two types of data that can be stored:</b>
- Data stored randomly by an application.
- Data stored about a samaritan.</br>

The database synchronizes the local db with the network periodically by asynchronously fetching the address of the latest data image from the contract and retrieving it from IPFS. It then updates the image, uploads the image and updates the contract.</br>Samaritans own the accesses to data stored about them by applications and can choose to revoke the accesses of these apps. That is performed implicitly by submitting a transaction and updating the state of the contract. In summary, it works like any normal key-value store but persists its data on IPFS nodes and gives the users the ability to control access to data stored about them by applications.
## Significance
SamaritanDB is very significant in the bid for a better internet. The fact that it is location independent and any single server, if located, cannot be shutdown to stop applications, means that anyone, like you could get the database and spin it up locally, redirect the applications built on it to fetch data from the local database, I MEAN THE LOCAL DATABASE YOU JUST DOWNLOADED! And its like you are online reading data like every other website when in fact you're running locally. You'll also be contributing and strengthening the network and data persistence and indistructability. So if the government or some Big Tech decides to shut you down, it would be virtually impossible. Also users can rest assured that data stored by applications about them is completely in their control.
SamaritanDB plays a big role in the SamOS ecosystem and our vision to give power completely to application developers and their users.

## Footnote
- Samaritan: This describes an individuals total online identity. Imagine various peices of paper joining to form a human collage. That human is a samaritan, representing the user on the internet.

We will never stop creating great products for a better internet.</br>
👋🏽 bis bald 👋🏽

&copy; Algorealm 2023
