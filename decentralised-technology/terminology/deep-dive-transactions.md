# Deep Dive: Transactions

_This chapter will formally define the term Bitcoin transaction._

Following the UTXO deep dive, I would like to clarify that UTXOs are not the transactions themselves. They are the inputs and outputs of a transaction.

**Breaking Down The Components of A Transaction**

> "txid": "8e7cf6b752bd7a33c95dc3b581b1bf0b325353855190b0e8e4e790486687e0ed",
>
> ```
> "version": 1,
>
> "locktime": 0,
> ```

**Transaction ID**

The txid is the unique identifier for a transaction. It is generated by hashing all of the other components in the transaction

_**Version Number: **_

Bitcoin is an evolving software, updates are made and new features are added. Remembering the elected person in the \_overview of Bitcoin, \_when verifying transactions, he needs to know whether there have been changes to the format of the transaction and whether new features have been added. This version number informs him of such details, as version one transactions follow certain rules.

**Locktime:**

The locktime is a feature which allows you to specify the earliest time, the elected person should include this transaction into the block. For example, if you specify that this transaction must only be included into the database on Monday 5th March 2019, then this transaction will sit inside of the unconfirmed transactions list, until that time. _Please note that the format for the date is unix. As we have not covered blocks as of yet. We will mention block locktime in a later chapter._

> "vin": \[
>
>     {
>
>         "txid": "40d9b71aecc36b2a276372702fbb9e6b31b259c67c183afec036e3b45052acf1",
>
>         "vout": 0,
>
>         "scriptSig":
>
>         {
>
>             "asm": "30440220561688bbd95013a817274f399fd7476f965f805904b886ac2cc2c291d883beed02201aa9467404c3dec4702468eee9c7bfe7940ea9531a8e5158b162ab5b705a6d22\[ALL\] 0399145f0981fcfefc8424b7730a71aa168b0b33389a88fb732257517c318c7ca5",
>
>             "hex": "4730440220561688bbd95013a817274f399fd7476f965f805904b886ac2cc2c291d883beed02201aa9467404c3dec4702468eee9c7bfe7940ea9531a8e5158b162ab5b705a6d2201210399145f0981fcfefc8424b7730a71aa168b0b33389a88fb732257517c318c7ca5"
>
>         },
>
>         "sequence": 4294967295,
>
>         "n": 0,
>
>         "addr": "1DJAbVv5MMRBnfqUqxpSAggi6RFjpgU25Z",
>
>         "value": 0.91837,
>
>     }\]

**VIN**

Remembering what we discussed in the UTXO chapter, VIN can be seen to be the individual notes, the **unspent transaction outputs. **In the above example, we have one, it is possible to have multiple inputs.  
  
**VIN: TXID**

In the UTXO chapter, we also discussed the concept of an input coming from another output, which is why it is named unspent transaction output. This transaction id, tells you the id for the transaction where this input was an output. In other words, If Alice is paying Bob and Charlie a combined amount of 5BTC. This transaction id, tells us which previous transaction Alice got the 5 BTC from.

**VIN : VOUT**

Now that we know what transaction Alice got this 5 BTC from. Vout tells you what position it is in the list of outputs. Remember, that if Alice wants to send 5BTC to Bob and to Charlie. This transaction will have multiple outputs. The first one being Bobs and the second being Charlies. Since Bob's transaction is first in the list, we say that his position is zero. Charlie's vout would be one.  
  
**ScriptSig:**
