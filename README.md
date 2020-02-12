# [Auctionity Saleroom](https://app.auctionity.com/) - [GraphQL API](https://graphql.org/) (v1.0.0-alpha)


## The GraphQL endpoint
```
https://api.auctionity.com
```

## Schema
[Auctionity - Saleroom GraphQL Schema](schema.graphql)

## Authentication
Authentication is provide by a [JWT (JSON Web Tokens)](https://jwt.io/introduction/) to get a token you have to sign a time-stamped message describe below.

### Login Request
```
Mutation:
login(message: String!, sign: String!, type: String): JWT!
```

- message =>  message must be `login/{current_timestamp}/{signer_address}` (ex: `login/1581501627/0x0000000000000000000000000000000000000000`)
- [eth_sign(message)](https://github.com/ethereum/wiki/wiki/json-rpc#eth_sign) -> (ex: `0x0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000`)
- type (optional) => if signature is provide par Trezor (type: `trezor`)


### Login Response
```
{
  "data": {
    "login": "xxxxx.yyyyy.zzzzz"
  }
}
```

Add HTTP Authorization request header
```
authorization: Bearer xxxxx.yyyyy.zzzzz
```