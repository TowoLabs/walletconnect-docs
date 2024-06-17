---
description: Litecoin JSON-RPC Methods
---

# Litecoin

## litecoin_sendTransfer

This method is used to sign and submit a transfer of any `amount` of Litecoin to a single `recipient`, optionally including a `memo` set as the OP_RETURN value by supporting wallets. The transaction will be signed and broadcasted upon user approval. 

### Parameters
* `Object`
    * `recipient` : `String` - _(Required)_ The recipient's public address.
    * `amount` : `String` - _(Required)_ Positive amount of Litecoin to send, denominated in litoshis (Litecoin base unit).
    * `memo` : `String` - _(Optional)_ The OP_RETURN value as a hex string without 0x prefix, maximum 40 characters.

### Returns
* `Object` 
    * `tx_id` : `String` - The transaction id as a hex string without 0x prefix.

### Example
The example below specifies a simple transfer of 1.23 LTC (123000000 Litoshi).

```javascript
// Request
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "litecoin_sendTransfer",
    "params": {
        "recipient": "ltc1q8c6fshw2dlwun7ekn9qwf37cu2rn755u9ym7p0",
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

## litecoin_getBalance

This method is used to find the total and spendable balance for a Litecoin wallet. The spendable balance should be calculated as the total balance minus an estimated on-chain fee. The estimated on-chain fee can be calculated from a theoretical transaction spending all the user's UTXOs as inputs and generating two outputs.

### Parameters
* `Object`
    * No parameters.

### Returns
* `Object` 
    * `totalBalance` : `String` - The sum of all UTXOs amounts, denominated in litoshis.
    * `spendableBalance` : `String` - The sum of all UTXOs minus an estimated on-chain fee, denominated in litohis.

### Example
The example below specifies a request to fetch the user's balance.

```javascript
// Request
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "litecoin_getBalance",
    "params": {}
}

// Result
{
    "id": 1,
    "jsonrpc": "2.0",
    "result": {
        "totalBalance": "245000000",
        "spendableBalance": "244998500"
    }
}
```
