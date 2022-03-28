## Marker genesis

`Marker genesis` is a developer utility to easy running atlas blockchain testnets and related jobs around testnets.

Its main advantage over previous solutions is that it's able to create a `genesis.json` where all core conctracts are
already deployed in it.

We need to use the marker tool. For information on how to use the marker tool, please refer to [Marker](../../marker/Marker.md)

### Generating a genesis.json

Suppose "github.com/mapprotocol/atlas" is your project path.

cd marker config path : github.com/mapprotocol/atlas/marker/config to modify markerConfig.json.

First you need to config the markerConfig.json like this:

```shell
{
  "AdminAddress": "0x1c0edab88dbb72b119039c4d14b1663525b3ac15",
  "Validators": [
    {
      "Address": "0x1c0eDab88dbb72B119039c4d14b1663525b3aC15",
      "PublicKeyHex": "0x0491c373a1504d67e0c6c98276fc6043544fd09a623473b6936a107943baf666612b5e2a3beacf839d1ec74fd00f4388d4b813eac26b26ab4859003473b286650a",
      "BLSPubKey": "0x82b9df317d21429c6f0b74c96c21a610483be1d234c2815c50be454a689c35ae01",
      "BLSProofOfPossession": "0x01549fe9a666f283bfc9f7217675ea86a7db91dfce7745aaef0a8850f993cf7bb1036b8740d7646ef9fb33f4f7b12183ee74b4ea7d0f51fb8b99ddb27b4bf414a81eaaaa551df6920c7d41179adfbf33e4e17cc33f874849d6a7493f0f4e1d86c3590ef385d8b5455edde052d363207b654402cff0113aa2ae1f3c0d293e4e68ad"
    },
    {
      "Address": "0x16FdBcAC4D4Cc24DCa47B9b80f58155a551ca2aF",
      "PublicKeyHex": "0x04e7678fb997c00d5998f79413d73ebde98865cd0d7fa82e2ab6d0920a72204d8c49c14f873ec9ee0e0b38651001acc9a4c1a0a63de6c6589b896f21f6a6bb6837",
      "BLSPubKey": "0x32071fff6599fcdefb78d8048abf7d32165e4dad0a00d7667ba4e1933a6f1bff00",
      "BLSProofOfPossession": "0x012adc9e784bbb9088d48860ca8f47583952ffc08b51f0101a79d02958fe297f6d2fed91b96dd527f8160d78c1465b3a78209043d556da9b66c445bdc58568395879d016852d708c6e645cbdbb0876aa4baff5ce3ab96cad2fa1c64c5c531e377100ed79b2ff00e4ea13c89bd6917356d3dcae3f9ce5b6a0199edef6de74549b44"
    },
    {
      "Address": "0x2dC45799000ab08E60b7441c36fCC74060Ccbe11",
      "PublicKeyHex": "0x04ec7664543f2dae218176a072ca7bfc16632438793077c06cf05975cc1302ee60c27f29e2cc3b64ffbaa69d2939e937f99a7bf93d7c5fa59bffbcd769e4f234e8",
      "BLSPubKey": "0x66b74fbfc9c23963a9a21e12d79422fc288b7598b58f23d4ec04ea2657a05a9901",
      "BLSProofOfPossession": "0x016e29b185836f0ab89bbbfab10cf2723d68606a889dceee94ff0f591a9c4a0feb2e5bd9d65c22cd25c9af3d59ad05185426f43d0b54af13a0ca1f15678d0ee32e0ea54ec4cbc7b4ae2ce4734b95cf46d754e321ea1cd876b6debe7c881b7541e7317f5d3bafdb4a75c7f7ffeb061b8fc2cc1e886cd1aab643b87973434e17d526"
    },
    {
      "Address": "0x6C5938B49bACDe73a8Db7C3A7DA208846898BFf5",
      "PublicKeyHex": "0x04ef2af91ba2fc2b04bc47c7d59d6d07a0dea2a62c5b537d4a83a387bee44245317de753c4e45858708c0d31473c6595ac9dddbcf7ac02a13df4af1a188e2c9c24",
      "BLSPubKey": "0x40cdae9b90b80179ac73341dd83974fa6dd85f921080770241df8b4f3eb2244e01",
      "BLSProofOfPossession": "0x011429fe83a89f7b314ba6454197ddc52d75c3d102f05475880791ab5f104a3f4f882fab6289d39ac38d0821afb2fcbbfb2b3ec0f8b07614d8187141e75ccdde2c6ad1b55825ed085a605d78019a4156d355a6dc0f25e9f2e568b075caad82c31609468a87f2b3270f04a23ee2574449b409a4b566a00b906c447fed0916c10111"
    }
    ...
  ]
}


```

Second you need compile your `map-contracts` project,we need the bytecode about `map-contracts` to make `genesis.json` file.

1.Download `map-contracts` project in any folder you like , use this command `git clone https://github.com/mapprotocol/map-contracts.git`

2.Suppose you have installed node, then then switch to the project file initialize the project and use this command `npm install`

3.Compile the project using truffle, the command compiled by truffle is `truffle compile`

4.A file called `build` will be generated in your `map-contracts` project. We will use this file to specify the corresponding parameters.

then to do so run:

```shell
USAGE
  $ ./Marker genesis

OPTIONS
  --buildpath                                                  buildpath is the path to 
                                                               truffle compile output folder.
  
  --newenv                                                     the genesis.json will be 
                                                               generated under this folder 

  --markercfg                                                  this your markerConfig.json 
                                                               path default to github.com/
                                                               mapprotocol/atlas/marker/config/
                                                               markerConfig.json
                                                     
  
EXAMPLES:

marker genesis --buildpath ./root/map-contracts/build/contracts --newenv ./root/atlasEnv --markercfg "./root/atlas/marker/config/markerConfig.json"


This will create a `genesis.json` in the ./root/atlasEnv folder
```
