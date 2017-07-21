### FintechWeek 2017 London Hackathon - Ethereum Token Challenge

This is just an example, you don't need to use the code included in this repository to build your application, but we believe that this could help you start trying/developing Ethereum apps quickly.

##### Please see the [Challenge PDF included in this repository](https://github.com/appliedblockchain/ftw_2017_challenge/blob/master/challenge-presentation.pdf) and more importantly the [Step-by-Step guide](https://github.com/appliedblockchain/ftw_2017_challenge/blob/master/FTW-ERC20-hackathon-screen-by-screen.pdf) useful if you're not familiar with Ethereum.

Also check the `index.html` file included in this repository.

---

#### General Guidelines

1. Install Metamask (If you have metamask installed use another browser or be sure to backup all your keys as metamask is based on an hd seed wallet but also imports keys)


2. Create a Github [Gist](https://gist.github.com) with your Metamask ethereum address [Switching from mainnet] - ( https://gist.github.com/YOUR_USER/COMMIT )


3. Visit the Testnet Faucet and claim your test Ethers: [faucet.rinkeby.io](https://faucet.rinkeby.io/)


4. Check the transaction for confirmation ( https://rinkeby.etherscan.io/address/YOUR_ADDRESS )

<!-- https://rinkeby.etherscan.io/address/0x5f0bc362b192f9305337320fc06d5c540d65114a -->

5. Deploy the (ERC20) token contract (open index.html with metamask unlocked [w/ Rinkeby Network Selected] and and hit the deploy button)


6. Test it (send tokens) 

notes: the two "blockchain" functions to use tokens are `new()`: the token creation function, `transfer()`:  the function that allows token holders to transfer funds between themselves (`transfer(to, amount)`)


####  new()

(js example: `TokenContract = TokenContract.at(localStorage.ftw_token_address); TokenContract.new({ /* ... */ })`) 

new() contains a line of code in solidity `balance[owner] = _initialSupply;` which assigns the user in its balance the full amount of the tokens ever created - after that the owner - owner being your metamask address that executed the Contract Deploy function (pressed the button and paid for gas for transaction)



####  transfer()

 (`transfer(to, amount)`)

(js example: `address = "0x1234"; tokenContract.transfer(address, 100)`) 

transfer() modifies the contract balance of the users simply substracting the balance from the previous owner and adding it to the next one

(solidity: 
```js
balances[msg.sender] -= _amount;
balances[_to] += _amount;

```
) 



7. Build something with the informations contained in this repository and in the pdf guide! [Step-by-Step guide](https://github.com/appliedblockchain/ftw_2017_challenge/blob/master/FTW-ERC20-hackathon-screen-by-screen.pdf) 


---

#### Extra

You can also check the newest ERC23.3 (ERC233) token here: https://github.com/Dexaran/ERC23-tokens/tree/Recommended


<!-- [adv.] TIP: in index.html, open the console and use localStorage.ftw_token_address = "0x1234" to reset your token to an arbitrary value if you need to reload a key -->


<!-- NOTE: customise your token - note - in index.html there is a FintechWeekToken (symbol: FTW) already compiled and ready to use -->

<!-- example on how to customise a standard token contract (https://gist.github.com/makevoid/ec7f9d94fdeb78d06cea48a17a117213 - ERC20) :

// (from step-by-step slides)

// ...

contract FixedSupplyToken is ERC20Interface {
   string public constant symbol = "YTO";
   string public constant name = "Your Token";
   uint8 public constant decimals = 18;
   uint256 _totalSupply = 1000000;

   // Owner of this contract
   address public owner;

   // Balances for each account
   mapping(address => uint256) balances;

   // .....

 -->


#### related:

Blockchain Week 17 Hackaton

https://appliedblockchain.github.io/bw-hackathon/
