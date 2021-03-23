# Matic Smart Contracts

## Testing:
Add a testETHAccounts.json to the root directory containing an array of at least 3 objects, each with a "privateKey" attribute that stores a private key for an account.
Then, run:
```
npm run test
```

## Stars Token
The Stars token is an ERC20 token used in Mogul Productions as an in-app currency, access token, and to vote for movie funding and other governance procedures.

### Functionality
- Burnable: Users can burn their own tokens and tokens approved by another user.
- Pausable: Admin can pause the transfer and burning of all tokens.
- Inflation: Each year, admin can choose to mint up to 4% of total supply, with initial supply being 400 million.
- Admin Change: Admin change give the admin role to another address at any time.

## Access Pass Sale
A contract that sells Stars to users with multiple tiers for purchase.

### Functionality
- Tiers: In order to purchase Stars, users must specify a tier to buy from. Each tier contains a specified number of access passes, which indicates how many times this tier can be purchased from. Each tier also has a specified price, and it has a specified number of Stars that is sent to the buyer upon purchase. A tier can be paused, which stops users from purchasing passes from that tier.
- Setting tiers: When changing a tier, if the new tier allows for the sale of more Stars than the tier currently does, the contract transfers the extra tokens it needs from the caller. Conversely, if the new tier allows for the sale of fewer Stars, the smart contract sends the caller the stars that it no longer needs.
- Withdrawing from tiers: reducePassesFromTiers reduces the specified amounts of access passes from each tier, and sends the tokens it no longer needs to the withdrawWallet. removeTiers does the same, except it withdraws all access passes from the specified tiers.


## Mogul Smart Wallet
A non-custodial smart contract based wallet that holds user funds and can be recovered by guardian accounts.

### Functionality
- Guardians: Account addresses that the wallet owner trusts to reset the owner address. Guardians can vote for a new owner to be in control of the smart wallet. Mogul Productions and a trusted third party security service will be readily available as a Guardian. Guardians can be added or removed by the owner.
- Change Owner Proposal: Guardians can create a proposal to change owner. The proposals can be voted on by Guardians, and when a minimum amount of votes (set by the owner) are reached, the proposal will go through. Only one proposal can be active at a time.
- Lock Wallet: In case of private key of an owner address being compromised, the owner can lock their wallet for 14 days. This will block the owner from performing any actions with their wallet, including token transfers, adding or removing Guardians and changing minimum vote count. This allows time for the Guradian accounts to vote to assign another address for the owner.



## Mogul Smart Wallet Factory
A proxy contract that deterministically deploys a smart wallet.

### Functionality
- Predict address: Smart wallet addresses can be predicted by passing in a salt as parameter. Given the same salt, the address will be the same every time its called. The address is also uniquely reserved for smart wallets deployed by this contract
- Deploy: Smart wallet is deployed to the predicted address
- Change Owner: The factory owner can be changed to another address. Only the owner can use the factory contract.
