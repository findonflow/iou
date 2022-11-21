# IOU

An IOU is a promise that a sender will send X amount of FT to a recipient.  

The core concept here is an *IOU*. It has the following semantics
 - an IOU is created from a resource stored in a users storage (to guarantee sender)
 - an IOU has the capablity to a receiver that is **immutable**, this guarnatees that the funds will **always** go to the intended receipient. It cannot be transferred to another user.
 - an IOU has a Type that corresponds to the DUC/FUT vaults
 - an IOU has an amount that can be updated since an IOU can be topped up
 - an IOU has an expiry date, the IOU contract will guarnatee that withdraw after this amount will panic and fail

See the following diagrams for an example flow
## Diagrams

![bid](out/bid/bid.png)

![increaseBid](out/increaseBid/increaseBid.png)

![fulfill](out/fulfillBid/fulfillBid.png)


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
 
