PyCu

Bitcoin application framework

Functions:

1. Simple interface in standard formats
2. No classes
3. Indenpendent functions
4. Supports binary, hex and base58
5. Transaction deserialization format almost compatible with BitcoinJS
6. Electrum and BIP0032 support
7. Make and publish a transaction all in a single command line instruction
8. Includes non-bitcoin-specific conversion and JSON utilities

Fucntions to-be-made:

1. Make the platform integrate the full tree of nodes
2. Make the platfrom decentralized and not rely on centralized souces for blockchain operations

Command line example:

from pybitcointools import *
priv = sha256('some big long brainwallet password')
priv '57c617d9b4e1f7af6ec97ca2ff57e94a28279a7eedd4d12a99fa11170e94f5a4'
pub = privtopub(priv)
pub '0420f34c2786b4bae593e22596631b025f3ff46e200fc1d4b52ef49bbdc2ed00b26c584b7e32523fb01be2294a1f8a5eb0cf71a203cc034ced46ea92a8df16c6e9'
addr = pubtoaddr(pub)
addr '1CQLd3bhw4EzaURHbKCwM5YZbUQfA4ReY6'
h = history(addr)
h [{'output': u'97f7c7d8ac85e40c255f8a763b6cd9a68f3a94d2e93e8bfa08f977b92e55465e:0', 'value': 50000, 'address': u'1CQLd3bhw4EzaURHbKCwM5YZbUQfA4ReY6'}, {'output': u'4cc806bb04f730c445c60b3e0f4f44b54769a1c196ca37d8d4002135e4abd171:1', 'value': 50000, 'address': u'1CQLd3bhw4EzaURHbKCwM5YZbUQfA4ReY6'}]
outs = [{'value': 90000, 'address': '16iw1MQ1sy1DtRPYw3ao1bCamoyBJtRB4t'}]
tx = mktx(h,outs)
tx '01000000025e46552eb977f908fa8b3ee9d2943a8fa6d96c3b768a5f250ce485acd8c7f7970000000000ffffffff71d1abe4352100d4d837ca96c1a16947b5444f0f3e0bc645c430f704bb06c84c0100000000ffffffff01905f0100000000001976a9143ec6c3ed8dfc3ceabcc1cbdb0c5aef4e2d02873c88ac00000000'
tx2 = sign(tx,0,priv)
tx2 '01000000025e46552eb977f908fa8b3ee9d2943a8fa6d96c3b768a5f250ce485acd8c7f797000000008b483045022100dd29d89a28451febb990fb1dafa21245b105140083ced315ebcdea187572b3990220713f2e554f384d29d7abfedf39f0eb92afba0ef46f374e49d43a728a0ff6046e01410420f34c2786b4bae593e22596631b025f3ff46e200fc1d4b52ef49bbdc2ed00b26c584b7e32523fb01be2294a1f8a5eb0cf71a203cc034ced46ea92a8df16c6e9ffffffff71d1abe4352100d4d837ca96c1a16947b5444f0f3e0bc645c430f704bb06c84c0100000000ffffffff01905f0100000000001976a9143ec6c3ed8dfc3ceabcc1cbdb0c5aef4e2d02873c88ac00000000'
tx3 = sign(tx2,1,priv)
tx3 '01000000025e46552eb977f908fa8b3ee9d2943a8fa6d96c3b768a5f250ce485acd8c7f797000000008b483045022100dd29d89a28451febb990fb1dafa21245b105140083ced315ebcdea187572b3990220713f2e554f384d29d7abfedf39f0eb92afba0ef46f374e49d43a728a0ff6046e01410420f34c2786b4bae593e22596631b025f3ff46e200fc1d4b52ef49bbdc2ed00b26c584b7e32523fb01be2294a1f8a5eb0cf71a203cc034ced46ea92a8df16c6e9ffffffff71d1abe4352100d4d837ca96c1a16947b5444f0f3e0bc645c430f704bb06c84c010000008c4930460221008bbaaaf172adfefc3a1315dc7312c88645832ff76d52e0029d127e65bbeeabe1022100fdeb89658d503cf2737cedb4049e5070f689c50a9b6c85997d49e0787938f93901410420f34c2786b4bae593e22596631b025f3ff46e200fc1d4b52ef49bbdc2ed00b26c584b7e32523fb01be2294a1f8a5eb0cf71a203cc034ced46ea92a8df16c6e9ffffffff01905f0100000000001976a9143ec6c3ed8dfc3ceabcc1cbdb0c5aef4e2d02873c88ac00000000'
pushtx(tx3) 'Transaction Submitted'

Command line exaple using kutool:

pybtctool random_electrum_seed 484ccb566edb66c65dd0fd2e4d90ef65

pybtctool electrum_privkey 484ccb566edb66c65dd0fd2e4d90ef65 0 0 593240c2205e7b7b5d7c13393b7c9553497854b75c7470b76aeca50cd4a894d7

pybtctool electrum_mpk 484ccb566edb66c65dd0fd2e4d90ef65 484e42865b8e9a6ea8262fd1cde666b557393258ed598d842e563ad9e5e6c70a97e387eefdef123c1b8b4eb21fe210c6216ad7cc1e4186fbbba70f0e2c062c25

pybtctool bip32_master_key 21456t243rhgtucyadh3wgyrcubw3grydfbng xprv9s21ZrQH143K2napkeoHT48gWmoJa89KCQj4nqLfdGybyWHP9Z8jvCGzuEDv4ihCyoed7RFPNbc9NxoSF7cAvH9AaNSvepUaeqbSpJZ4rbT

pybtctool bip32_ckd xprv9s21ZrQH143K2napkeoHT48gWmoJa89KCQj4nqLfdGybyWHP9Z8jvCGzuEDv4ihCyoed7RFPNbc9NxoSF7cAvH9AaNSvepUaeqbSpJZ4rbT 0
xprv9vfzYrpwo7QHFdtrcvsSCTrBESFPUf1g7NRvayy1QkEfUekpDKLfqvHjgypF5w3nAvnwPjtQUNkyywWNkLbiUS95khfHCzJXFkLEdwRepbw 

pybtctool bip32_privtopub xprv9s21ZrQH143K2napkeoHT48gWmoJa89KCQj4nqLfdGybyWHP9Z8jvCGzuEDv4ihCyoed7RFPNbc9NxoSF7cAvH9AaNSvepUaeqbSpJZ4rbT
xpub661MyMwAqRbcFGfHrgLHpC5R4odnyasAZdefbDkHBcWarJcXh6SzTzbUkWuhnP142ZFdKdAJSuTSaiGDYjvm7bCLmA8DZqksYjJbYmcgrYF

Command line options:

The -s option lets you read arguments from the command line

The -b option lets you read binary data as an argument

The -j option lets you read json from the command line (-J to split a json list into multiple arguments)

Main commands:

* privkey_to_pubkey    : (privkey) -> pubkey
* privtopub            : (privkey) -> pubkey
* pubkey_to_address    : (pubkey) -> address
* pubtoaddr            : (pubkey) -> address
* privkey_to_address   : (privkey) -> address
* privtoaddr           : (privkey) -> address

* add                  : (key1, key2) -> key1 + key2 (works on privkeys or pubkeys)
* multiply             : (pubkey, privkey) -> returns pubkey * privkey

* ecdsa_sign           : (message, privkey) -> sig
* ecdsa_verify         : (message, sig, pubkey) -> True/False
* ecdsa_recover        : (message, sig) -> pubkey

* random_key           : () -> privkey
* random_electrum_seed : () -> electrum seed

* electrum_stretch     : (seed) -> secret exponent
* electrum_privkey     : (seed or secret exponent, i, type) -> privkey
* electrum_mpk         : (seed or secret exponent) -> master public key
* electrum_pubkey      : (seed or secexp or mpk) -> pubkey

* bip32_master_key     : (seed) -> bip32 master key
* bip32_ckd            : (private or public bip32 key, i) -> child key
* bip32_privtopub      : (private bip32 key) -> public bip32 key
* bip32_extract_key    : (private or public bip32_key) -> privkey or pubkey

* deserialize          : (hex or bin transaction) -> JSON tx
* serialize            : (JSON tx) -> hex or bin tx
* mktx                 : (inputs, outputs) -> tx
* mksend               : (inputs, outputs, change_addr, fee) -> tx
* sign                 : (tx, i, privkey) -> tx with index i signed with privkey
* multisign            : (tx, i, script, privkey) -> signature
* apply_multisignatures: (tx, i, script, sigs) -> tx with index i signed with sigs
* scriptaddr           : (script) -> P2SH address
* mk_multisig_script   : (pubkeys, k, n) -> k-of-n multisig script from pubkeys
* verify_tx_input      : (tx, i, script, sig, pub) -> True/False
* tx_hash              : (hex or bin tx) -> hash

* history              : (address1, address2, etc) -> outputs to those addresses
* unspent              : (address1, address2, etc) -> unspent outputs to those addresses
* fetchtx              : (txash) -> tx if present
* pushtx               : (hex or bin tx) -> tries to push to blockchain.info/pushtx

* access               : (json list/object, prop) -> desired property of that json object
* multiaccess          : (json list, prop) -> like access, but mapped across each list element
* slice                : (json list, start, end) -> given slice of the list
* count                : (json list) -> number of elements
* sum                  : (json list) -> sum of all values

Forked from Python Bitcoin Tools