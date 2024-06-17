---
description: Bitcoin JSON-RPC Methods
---

# Bitcoin

## bitcoin_sendTransfer

This method is used to sign and submit a transfer of any `amount` of Bitcoin to a single `recipient`, optionally including a `memo` set as the OP_RETURN value by supporting wallets. The transaction will be signed and broadcasted upon user approval. 

### Parameters
* `Object`
    * `recipient` : `String` - _(Required)_ The recipient's public address.
    * `amount` : `String` - _(Required)_ Positive amount of Bitcoin to send, denominated in satoshis (Bitcoin base unit).
    * `memo` : `String` - _(Optional)_ The OP_RETURN value as a hex string without 0x prefix, maximum 40 characters.

### Returns
* `Object` 
    * `tx_id` : `String` - The transaction id as a hex string without 0x prefix.

### Example
The example below specifies a simple transfer of 1.23 BTC (123000000 Satoshi).

```javascript
// Request
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "bitcoin_sendTransfer",
    "params": {
        "recipient": "bc1qwz2lhc40s8ty3l5jg3plpve3y3l82x9l42q7fk",
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
