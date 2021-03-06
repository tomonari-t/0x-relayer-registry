# 0x Relayer Registry

A collection of relayers built on [0x](https://0xproject.com/) and their corresponding metadata.

Addition to this repository is not a requirement to use the 0x Protocol. It's intended to make it easier for traders and developers to find [SRA-Compliant](https://github.com/0xProject/standard-relayer-api/blob/master/README.md) relayers and take advantage of networked liquidity, as well as for users to find a relayer to start trading on.

## Usage

Option A. Clone this repo and import `relayers.json` into your own project or  
Option B. Get the latest version by fetching it directly from this repo
`$ curl -i -H "Accept: application/json" https://api.github.com/repos/0xProject/0x-relayer-registry/contents/relayers.json?client_id={CLIENT_ID}&client_secret={CLIENT_SECRET}`

Entries that have values for `sra_http_endpoint` or `sra_ws_endpoint` comply with the [Standard Relayer API](https://github.com/0xProject/standard-relayer-api/blob/master/README.md). These endpoints can be easily queried using [0x Connect](https://github.com/0xProject/0x-monorepo/tree/development/packages/connect).

## Submission Process

1.  Fork this repository.
2.  Add your logo image in a web-safe format (GIF, JPEG, or PNG) to the `images\logos` folder.
3.  Add a header image for promotional display in the [0x portal](https://0xproject.com/portal) in a web-safe format (GIF, JPEG, or PNG) to the `images\headers` folder. The header image should be 683x384 or larger, following a 16:9 ratio.
4.  Install [yarn](https://yarnpkg.com) and run `yarn install`
5.  Generate a UUID for your relayer by running `yarn generate:uuid`.
6.  Add an entry to `relayers.json` that complies with the Relayer JSON Schema in [`schemas.ts`](./schemas.ts)
7.  Run `yarn test` to verify that the updated `relayers.json` file passes schema validation.
8.  Submit PR for approval

A sample submission:

```json
"8ed099da-775b-4fd0-9b1e-f622d8db9039": {
    "name": "Sample Relayer",
    "homepage_url": "https://asamplewebsite.com",
    "app_url": "https://app.asamplewebsite.com",
    "header_img": "samplerelayerheader.png",
    "logo_img": "samplerelayerlogo.png",
    "networks": [
        {
            "networkId": 1,
            "sra_http_endpoint": "https://api.asamplewebsite.com/",
            "sra_ws_endpoint": "ws://api.asamplewebsite.com",
            "static_order_fields": {
                "fee_recipient_addresses": ["0x1111111111111111111111111111111111111111"]
            }
        }
    ]
}
```

A full list of permitted fields can be found in the [schemas.ts](./schemas.ts) file.
