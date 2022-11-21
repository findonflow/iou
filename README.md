# IOU

An IOU is a promise that a sender will send X amount of FT to a recipient.  

The core concept here is an *IOU*. It has the following semantics
 - an IOU is created from a proxy resource stored in a users storage (to guarantee sender), user need to sign because we borrow from his storage
 - an IOU is created from a Vault of a type that only dapper can do, so dapper needs to sign.
 - an IOU has the capablity to a receiver that is **immutable**, this guarnatees that the funds will **always** go to the intended receipient. It cannot be transferred to another user.
 - an IOU has a Type that corresponds to the DUC/FUT vaults
 - an IOU has an amount that can be updated since an IOU can be topped up
 - an IOU has an expiry date, the IOU contract will guarnatee that withdraw after this time will panic and fail

See the following diagrams for an example flow
## Diagrams

Taxonomy:
 - blue rectangles are resources
 - orange rectangle is the new resource beeing proposed
 - white folders are events
 - white files are transactions
 - people are accounts
 - blue databases are vaults

The diagrams are added to the repo as PUML files written in https://plantuml.com/deployment-diagram syntax. Preview using VScode.

### Bob offers 100 FUT to Alice NFT
![bid](out/bid/bid.png)

### Bob increases bid with 10 FUT
![increaseBid](out/increaseBid/increaseBid.png)

### Alice Fulfills the Auction
![fulfill](out/fulfillBid/fulfillBid.png)

### Alice cancels the auction (alternate)
![cancel](out/cancelBid/cancelBid.png)

## Intended Usecase

Any solution that wants to reason about the guarnatee that an user has funds on Dapper Wallet. 
Examples:
 - Offers (both Direct and Global)
 - Auctions( both English, Dutch, Vickrey, Bucket)
 - Loans/Flowty
 
## What needs to be done off chain
 
 In order for this to work there needs to be an accounting solution that knows how to reason about the *IOU.IOUxxx* events that are emitted. 
 In adition there needs to be a routine that checks if IOUs are expired.
 
 
## Questions
In order to handle royalties aso in IOUs we need to create several of them or have them support multiple receivers with fractions. What model is the best?
