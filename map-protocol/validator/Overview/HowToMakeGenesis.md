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
  "AdminAddress": "0xF2638eeC80767D19BAEF5bA955a757a830BD8660",
  "Validators": [
    {
      "Address": "0xF2638eeC80767D19BAEF5bA955a757a830BD8660",
      "PublicKeyHex": "0x043b01a92c51b0291b6a7343bf57b4321345460ed0835e286c652b212204efe4ad1fae14048e7a0468842be1237be9cec6dfc3e743cf64ceb17fdb1f907385f2b6",
      "BLSPubKey": "0x2b4d8fe8ec4b901b774790576f754db17f2d3476879e4e69fba154477dcb01e0219171e58aec6ff3f73a79fe99a5c674920c01361aa15e79b3f23d0e301c84cc13cd2c19260ca91cb27817441ac454dcf1f141d438b0d63fe0308d298b5886f312ba3f8aa14420c741d5ca27570e20bdfb220f15b9dca5e8ddab98769b67c95d00",
      "BLSG1PubKey": "0x0c877b10815027af5e78c2332dd5a727f54deaa494b465d4c90ca0b04b73c48a00849eebd32caa72c49d7cdba04367abbfe8a0a499720cd0a8f703c9f3a4b45d0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
      "BLSProofOfPossession": "0x057ebd74facf42b3c31305093cbeb7d1129e17acd34254d64f7d99ab75dbfafe07d7abc3b8620dfd5c538afbc4a82f3e99e7981707f7ecc68f8e2ebf761398f1"
    },
    {
      "Address": "0x16FdBcAC4D4Cc24DCa47B9b80f58155a551ca2aF",
      "PublicKeyHex": "0x04e7678fb997c00d5998f79413d73ebde98865cd0d7fa82e2ab6d0920a72204d8c49c14f873ec9ee0e0b38651001acc9a4c1a0a63de6c6589b896f21f6a6bb6837",
      "BLSPubKey": "0x0a2e37ecad6e69bfec9fec2b345d0f8441a0f63acf8b45c0131a78e5d777d52e0a39404ca85f2c08752c1d4ff8df05c82c7880779d61fe3fabcd4fd682463c0515b1f0217561a6a72bd381da19e34c5560c6eccb08ff83d7d3f4ac6da7f5d1ed15a2780f782c1fa571fa65b99694af559b9df168b1d8745ac3bbc7d3fe550b9400",
      "BLSG1PubKey": "0x15b7bcf0accf839170a5d4621282edcf14f4a438f8e53abcead5f0528cb91cb1135fd4e82ede1493ab1209af122e1dc186c885cc96d2413cbc09a58163b91eb90000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
      "BLSProofOfPossession": "0x1d4c9856b3f6a0e064575a7587e4ab2ac7d39f40b2f66d5706d9f7e0e12da6500496cb344112c99bde4c3b2cd574ff38095821880c97b43f7244a07b8734fab5"
    },
    {
      "Address": "0x2dC45799000ab08E60b7441c36fCC74060Ccbe11",
      "PublicKeyHex": "0x04ec7664543f2dae218176a072ca7bfc16632438793077c06cf05975cc1302ee60c27f29e2cc3b64ffbaa69d2939e937f99a7bf93d7c5fa59bffbcd769e4f234e8",
      "BLSPubKey": "0x086fac850f3a9f36e8a5107eab0ba79044043dc2cc6b897cbbd0d4bf805570ff270a98f28e2d2e70b7b2ecc41a4a13e453178354997aa2038852c5945f0564bb02cdf57642881a1b40417fe3620429fc087f8dee6a68e5d7193d3243c38a1f3827d0f4cb616722a1fa78a283a17589d7688a769ade77e9d6417c6e2a9adf59c300",
      "BLSG1PubKey": "0x2fd433e93187f6b3d15664ec48073bd73d57c801c4a8bfc1e0e3abd3deefc45619d45ac7ad54df7dda5b8afd6f882c9d9f879dbc6d587f1da5da1751baac729f0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
      "BLSProofOfPossession": "0x1b4070c6693257ebdf05f850a15986b62acd0d98d75a16568e0d845ca78bc9ef2bc09e6e5ff5b59b6c66ab7816dd10db869a1bd5494c7fc4b999333e4196974c"
    },
    {
      "Address": "0x6C5938B49bACDe73a8Db7C3A7DA208846898BFf5",
      "PublicKeyHex": "0x04ef2af91ba2fc2b04bc47c7d59d6d07a0dea2a62c5b537d4a83a387bee44245317de753c4e45858708c0d31473c6595ac9dddbcf7ac02a13df4af1a188e2c9c24",
      "BLSPubKey": "0x03fea7bc386ea24aaa19c563a4f26f38cbc2ce172ba2310587405f4f05777fb911a4c3553b7b6529ea02a9da3ae2df6f70c3409105b39e1930d6a6ae8344fc221f5dfb2e73cc8ce434d1af33d95366796bdec26ca7cfcc0a03867fabf471884206db6b9e175a131995bd0c70b93a6f2eec96d831ad0c42d13d334f780d57883400",
      "BLSG1PubKey": "0x1b037f39d9f8e74b608a898249cc3d156ff1f0051026388366b85a84aac43bb4068275cd909e16b29f1b3bc97e91ec0a8b95a11b8a574cbc2c9ea142d26c8a490000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
      "BLSProofOfPossession": "0x09d18fce54efd8c980f2c214facef96ff948ac042068db4f9c7d2f93d61b520725f1781515415a8b7ef8b19964af5cba0eaef4b40e9edbeb609ab922f408ce8c"
    }
  ]
}



```

Second you need compile your `map-contracts` project,we need the bytecode about `map-contracts` to make `genesis.json` file.

Please refer to [Deployment of contract related to validator](../contracts/DeployContracts.md#deployment-of-contract-related-to-validator)

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
