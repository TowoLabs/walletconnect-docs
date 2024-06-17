---
description: Dogecoin JSON-RPC Methods
---

# Dogecoin

## dogecoin_sendTransfer

This method is used to sign and submit a transfer of any `amount` of Dogecoin to a single `recipient`, optionally including a `memo` set as the OP_RETURN value by supporting wallets. The transaction will be signed and broadcasted upon user approval. 

### Parameters
* `Object`
    * `recipient` : `String` - _(Required)_ The recipient's public address.
    * `amount` : `String` - _(Required)_ Positive amount of Dogecoin to send, denominated in satoshis (Dogecoin base unit).
    * `memo` : `String` - _(Optional)_ Hex string without 0x prefix, maximum 40 characters and will be sent as the OP_RETURN value.

### Returns
* `Object` 
    * `tx_id` : `String` - The transaction id as a hex-encoded string.

### Example
The example below specifies a simple transfer of 1.23 DOGE (123000000 Satoshi).

```javascript
/// Request
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "dogecoin_sendTransfer",
    "params": {
        "recipient": "DBcZSePDaMMduBMLymWHXhkE5ArFEvkagU",
        "amount": "123000000",
        "memo": "636861726c6579206c6f766573206865",
    }
}

// Result
{
    "id": 1,
    "jsonrpc": "2.0",
    "result": {
        "tx_id": "f007551f169722ce74104d6673bd46ce193c624b8550889526d1b93820d725f7"
    }
}
```
