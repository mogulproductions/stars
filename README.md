#  Smart Contracts


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

Find audit here: https://docsend.com/view/cmh5esuvv9ngnrkv

