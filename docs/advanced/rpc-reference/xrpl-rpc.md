---
description: XRPL JSON-RPC Methods
---

# XRPL

## xrpl_sendTransaction

This method is used to sign and send a transaction to the XRP Ledger. The basis of a transaction is defined by the [XRPL Transaction Common Fields][], it defines the properties that are available to all transaction types. The actual transactions that are supported on the XRPL can be found [here][XRPL Transaction Types]. It is expected that the parameters that are defined as `Required`, but not `auto-fillable` are provided by the dapp to the wallet.


### Parameters
1. `Object` - The [transaction][XRPL Transaction Types] to be executed.

### Returns
1. `Object` - JSON representation of the transaction sent to the XRPL.

### Example

```javascript
// Request
{
    "id": 1,
    "jsonrpc": "2.0",
    "method": "xrpl_sendTransaction",
    "params": {
        "TransactionType": "OfferCreate",
        "Account": "rMBzp8CgpE441cp5PVyA9rpVV7oT8hP3ys",
        "Fee": "10",
        "Flags": 524288,
        "LastLedgerSequence": 7108682,
        "Sequence": 8,
        "TakerGets": "15000000000",
        "TakerPays": {
            "currency": "USD",
            "issuer": "rvYAfWj5gh67oV6fW32ZzP3Aw4Eubs59B",
            "value": "7072.8"
        }
    }
}
// Result
{
    "id": 1,
    "jsonrpc": "2.0",
    "result": {
        "Account": "rMBzp8CgpE441cp5PVyA9rpVV7oT8hP3ys",
        "Expiration": 595640108,
        "Fee": "10",
        "Flags": 524288,
        "OfferSequence": 1752791,
        "Sequence": 1752792,
        "LastLedgerSequence": 7108682,
        "SigningPubKey": "03EE83BB432547885C219634A1BC407A9DB0474145D69737D09CCDC63E1DEE7FE3",
        "TakerGets": "15000000000",
        "TakerPays": {
            "currency": "USD",
            "issuer": "rvYAfWj5gh67oV6fW32ZzP3Aw4Eubs59B",
            "value": "7072.8"
        },
        "TransactionType": "OfferCreate",
        "TxnSignature": "30440220143759437C04F7B61F012563AFE90D8DAFC46E86035E1D965A9CED282C97D4CE02204CFD241E86F17E011298FC1A39B63386C74306A5DE047E213B0F29EFA4571C2C",
        "hash": "73734B611DDA23D3F5F62E20A173B78AB8406AC5015094DA53F53D39B9EDB06C"
    }
}
```

[XRPL Transaction Common Fields]: https://xrpl.org/transaction-common-fields.html
[XRPL Transaction Types]: https://xrpl.org/transaction-types.html
