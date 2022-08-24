# Preperation

```
solana config set --url https://api.devnet.solana.com

cp ./DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU.json ~/.config/solana/

solana config set -k ~/.config/solana/DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU.json

solana airdrop 2
```

# NFT bank

Generate CandyMachine by using Metaplex `Sugar` cli tool.

```
mkdir nft-bank
cd nft-bank
sugar launch
```

checkout the console output:

```
Starting Sugar launch... 🚀

>>> sugar validate

[1/1] 🗂  Loading assets
▪▪▪▪▪ Validating 3 metadata file(s)...

Validation complete, your metadata file(s) look good.

>>> sugar upload

[1/4] 🗂  Loading assets
Found 3 asset pair(s), uploading files:
+--------------------+
| images    |      3 |
| metadata  |      3 |
+--------------------+

[2/4] 🖥  Initializing upload
▪▪▪▪▪ Connected
Funding address:
  -> pubkey: DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU
  -> lamports: 39113 (◎ 0.000039113)
Signature: 412t5iyXGzBEeW78riT8BX3gVJyz3PLJE1BM2XCdb9VNSFvNiVYYpuN5Hs82b6Gqoi6u3YEBjV7AhuSEU6Q6Gi33

[3/4] 📤 Uploading image files

Sending data: (Ctrl+C to abort)
[00:00:02] Upload successful █████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████ 3/3

[4/4] 📤 Uploading metadata files

Sending data: (Ctrl+C to abort)
[00:00:00] Upload successful █████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████ 3/3

3/3 asset pair(s) uploaded.

>>> sugar deploy

[1/3] 🍬 Creating candy machine
Candy machine ID: 4pMtZrEmTKkmvQbj5hhfEv98GyHewFQHFxoNzK5WsN63

[2/3] 📦 Creating and setting the collection NFT for candy machine
Collection mint ID: 7nTcdJ8Cnvqh2k8r4MLvf4nDj4JajPgQE2QtLT3SjyL4

[3/3] 📝 Writing config lines
Sending config line(s) in 1 transaction(s): (Ctrl+C to abort)
[00:00:02] Write config lines successful █████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████ 1/1

>>> sugar verify

[1/2] 🍬 Loading candy machine
▪▪▪▪▪ Completed

[2/2] 📝 Verification
Verifying 2 config line(s): (Ctrl+C to abort)
[00:00:01] Config line verification successful ███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████ 2/2

Verification successful. You're good to go!

See your candy machine at:
  -> https://www.solaneyes.com/address/4pMtZrEmTKkmvQbj5hhfEv98GyHewFQHFxoNzK5WsN63devnet

✅ Command successful.
```

## Awesome Tool for Checking NFT on Solana

[Solanaeyes](https://www.solaneyes.com/address/4pMtZrEmTKkmvQbj5hhfEv98GyHewFQHFxoNzK5WsN63devnet)


# Check Results on SolanEyes

candy machine address
https://www.solaneyes.com/address/4pMtZrEmTKkmvQbj5hhfEv98GyHewFQHFxoNzK5WsN63

collection mint address
https://www.solaneyes.com/address/7nTcdJ8Cnvqh2k8r4MLvf4nDj4JajPgQE2QtLT3SjyL4

token mint address
https://www.solaneyes.com/address/GZZPxeFjCpQBzBodV79dEfY5Ar42738emJrPMsoUZrVy

token account (link to owner)
https://www.solaneyes.com/address/FQZB4XwmdfqDUWvdrwwuPia7CXyAHuAxU1PBiZEf7nJK

wallet account (NFT holder)
https://www.solaneyes.com/address/DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU

# Auction House

## Setup

```
git clone https://github.com/metaplex-foundation/deprecated-clis
yarn install
cd ./src
```

## Check CLI usage

```
ts-node auction-house-cli.ts help 
```

Response:

```
Usage: auction-house-cli create_auction_house [options]

Options:
  -e, --env <string>                                Solana cluster env name, i.e. mainnet-beta, testnet, devnet (default: "devnet")
  -k, --keypair <path>                              Solana wallet location (default: "--keypair not provided")
  -l, --log-level <string>                          log level
  -tm, --treasury-mint <string>                     Mint address of treasury. If not used, default to SOL.
  -sfbp, --seller-fee-basis-points <string>         Auction house cut of each txn, 10000 = 100%
  -ccsp, --can-change-sale-price <string>           if true, and user initially places item for sale for 0, then AH can make new sell prices without consent(off chain price matching). Should only be used in concert with requires-sign-off, so AH is controlling every txn
                                                    hitting the system.
  -rso, --requires-sign-off <string>                if true, no txn can occur against this Auction House without AH authority as signer. Good if you are doing all txns through a pass-through GCP or something.
  -twd, --treasury-withdrawal-destination <string>  if you wish to empty the treasury account, this is where it will land, default is your keypair. Pass in a wallet, not an ATA - ATA will be made for you if not present.
  -fwd, --fee-withdrawal-destination <string>       if you wish to empty the fee paying account, this is where it will land, default is your keypair
  -h, --help  
```

## Create

```
ts-node auction-house-cli.ts create_auction_house --keypair ../../DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU.json -e devnet -sfbp 500 -ccsp false -rso false
```

- `sfbp` (seller-fee-basis-points): 5%
- `ccsp` (can-change-sale-price): false, becuase we're setup a centralized marketplace.

Response:

```
wallet public key: DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU
Using cluster devnet
No treasury withdrawal dest detected, using keypair
No fee withdrawal dest detected, using keypair
No treasury mint detected, using SOL.
Created auction house 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR
```

## Show

```
ts-node auction-house-cli.ts show -k ../../DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU.json -ah 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR
```

Response:

```
wallet public key: DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU
Using cluster devnet
No treasury mint detected, using SOL.
-----
Auction House: 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR
Mint: So11111111111111111111111111111111111111112
Authority: DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU
Creator: DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU
Fee Payer Acct: DFHKCxjSWjAt5LjYvRYxCK3CgP8sEG5KYf2Lq6mwaZ25
Treasury Acct: H1MkDgjA92f5J6WbCw5WabyaxL7tyS1zPFAC4QNA1Kr3
Fee Payer Withdrawal Acct: DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU
Treasury Withdrawal Acct: DEV2rZ8hZ7TokaXyd29ShobdL3aeDHyja8wnsREJWEiU
Fee Payer Bal: 0
Treasury Bal: 0
Seller Fee Basis Points: 500
Requires Sign Off: false
Can Change Sale Price: false
AH Bump: 254
AH Fee Bump: 255
AH Treasury Bump: 254
```

## Sell

In this case, use `C9mzyfKqwPtjqK3CrNsij7syyQvr6XKquEHrnM22wa9Z` as seller.

```
ts-node auction-house-cli.ts sell \
  -k ~/.config/solana/C9mzyfKqwPtjqK3CrNsij7syyQvr6XKquEHrnM22wa9Z.json \
  -ah 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR \
  --buy-price 0.5 \
  --mint GZZPxeFjCpQBzBodV79dEfY5Ar42738emJrPMsoUZrVy \
  --token-size 1 \
  -l trace
```

```
setting the log value to: trace
wallet public key: C9mzyfKqwPtjqK3CrNsij7syyQvr6XKquEHrnM22wa9Z
Using cluster devnet
Started awaiting confirmation for LpDunYGMuysfLL6vhe3nckUTTS6MwijshmH2o3ijZZouU4WSXZqHWJes73nArjiGDcx6WhPC2Ry6pFJWDGkH19e
REST null result for LpDunYGMuysfLL6vhe3nckUTTS6MwijshmH2o3ijZZouU4WSXZqHWJes73nArjiGDcx6WhPC2Ry6pFJWDGkH19e null
Resolved via websocket { err: null }
Returning status { err: null, slot: 157087704, confirmations: 0 }
Latency (ms) LpDunYGMuysfLL6vhe3nckUTTS6MwijshmH2o3ijZZouU4WSXZqHWJes73nArjiGDcx6WhPC2Ry6pFJWDGkH19e 1.7400000095367432
Set 1 GZZPxeFjCpQBzBodV79dEfY5Ar42738emJrPMsoUZrVy for sale for 0.5 from your account with Auction House 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR
```

## Buy

```
ts-node auction-house-cli.ts buy \
  -k ~/.config/solana/Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu.json \
  -ah 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR \
  --buy-price 1.2 \
  --token-size 1 \
  --mint GZZPxeFjCpQBzBodV79dEfY5Ar42738emJrPMsoUZrVy
```

```
wallet public key: Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu
Using cluster devnet
Made offer for  1.2
```

### explore `Buy` transaction

tx:
https://solscan.io/tx/4zoL59X7emkpMYJURN7xRLa8oBni5Ghi8BkKqVSCwpwwPNnn8eupXj5j2tcVaQSfLFFAbBiWFhTrXvUxW7PTFJPP?cluster=devnet

Escrow Payment Account:
`HADtbXY6ejqBtUwdtVPsEugrLXm73cHzvwFjdJegaQtm`

## Cancel - Buy

```
ts-node auction-house-cli.ts cancel \
  -k ~/.config/solana/Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu.json \
  -ah 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR \
  --buy-price 1.2 \
  --token-size 1 \
  --mint GZZPxeFjCpQBzBodV79dEfY5Ar42738emJrPMsoUZrVy
```

```
wallet public key: Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu
Using cluster devnet
Cancelled buy or sale of 1 GZZPxeFjCpQBzBodV79dEfY5Ar42738emJrPMsoUZrVy for 1.2 from your account with Auction House 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR
```

## Withdraw

After cancel the Buy request, perform `withdraw` request to withdraw tokens from Auction House.

```
ts-node auction-house-cli.ts withdraw -k ~/.config/solana/Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu.json -ah 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR -a 2
```

Response:

```
wallet public key: Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu
Using cluster devnet
Withdrew 2000000000 from your account with Auction House 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR . New Balance: 890880
```

## Execute Sale

* Note: the `buy-price` must be the same in **Buy** and **Sell** request.
* To run this case, we must send a new **Buy** request with `0.5` for `buy-price`.

```
ts-node auction-house-cli.ts execute_sale \
  -k ~/.config/solana/Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu.json \
  -ah 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR \
  --buy-price 0.5 \
  --mint GZZPxeFjCpQBzBodV79dEfY5Ar42738emJrPMsoUZrVy \
  --buyer-wallet Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu \
  --seller-wallet C9mzyfKqwPtjqK3CrNsij7syyQvr6XKquEHrnM22wa9Z \
  --token-size 1 \
  -l trace
```

```
setting the log value to: trace
wallet public key: Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu
Using cluster devnet
Started awaiting confirmation for 5qhM25EoPyVqvfW3U81Timw4QGybJrTmiL5kZrgE7F33EZpDvRPRj5CrvARR5kgC7QqJVRdjDDJexrnLCxXZRBuL
REST null result for 5qhM25EoPyVqvfW3U81Timw4QGybJrTmiL5kZrgE7F33EZpDvRPRj5CrvARR5kgC7QqJVRdjDDJexrnLCxXZRBuL null
Resolved via websocket { err: null }
Returning status { err: null, slot: 157180441, confirmations: 0 }
Latency (ms) 5qhM25EoPyVqvfW3U81Timw4QGybJrTmiL5kZrgE7F33EZpDvRPRj5CrvARR5kgC7QqJVRdjDDJexrnLCxXZRBuL 1.3989999294281006
Accepted 1 GZZPxeFjCpQBzBodV79dEfY5Ar42738emJrPMsoUZrVy sale from wallet C9mzyfKqwPtjqK3CrNsij7syyQvr6XKquEHrnM22wa9Z to Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu for 0.5 from your account with Auction House 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR
```



# FAQ

## `index out of bounds` error

This might occured when we sending the parameters but unable to find the matched data.

e.g. Cancel with wrong `buy-price` value.

```
ts-node auction-house-cli.ts cancel \
  -k ~/.config/solana/Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu.json \
  -ah 9z666zc3Pm7h5XzK2wFxLDFUse7kxF53ms932US5RemR \
  --buy-price 1.2 \
  --token-size 1 \
  --mint GZZPxeFjCpQBzBodV79dEfY5Ar42738emJrPMsoUZrV
```

```
wallet public key: Egu83sufo3ZdvwAo8MUN2YPX2jRuJ9aUzmBoRhLMPUvu
Using cluster devnet
Rejected via websocket { InstructionError: [ 0, 'ProgramFailedToComplete' ] }
Timeout Error caught {
  err: { InstructionError: [ 0, 'ProgramFailedToComplete' ] },
  slot: 157178088,
  confirmations: 0
}
/Users/joecwu/projects/crypto/solfren/issue-nft/deprecated-clis/src/helpers/transactions.ts:136
            throw new Error(
                  ^
Error: Transaction failed: panicked at 'index out of bounds: the len is 0 but the index is 0', src/cancel/mod.rs:201:19
    at sendSignedTransaction (/Users/joecwu/projects/crypto/solfren/issue-nft/deprecated-clis/src/helpers/transactions.ts:136:19)
    at processTicksAndRejections (node:internal/process/task_queues:96:5)
    at async sendTransactionWithRetryWithKeypair (/Users/joecwu/projects/crypto/solfren/issue-nft/deprecated-clis/src/helpers/transactions.ts:59:26)
    at async Command.<anonymous> (/Users/joecwu/projects/crypto/solfren/issue-nft/deprecated-clis/src/auction-house-cli.ts:638:5)
```