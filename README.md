# DeFi-Project
Launch your own crypto-currency
In this project, we are going to :
1) Create our own cryptocurrency.
2) Create and mint tokens.
3) Learn how to mint the tokens.
4) Learn how to distribute your tokens to other people.

Pre-requisites:
1) Solana installed on your computer.
2) Some command-line experiance 

You have to install Solana. So to install solana, follow the below link and install it:
https://github.com/LearnWithArjun/solana-env-setup

Those of you who are using Windows and whose versions are less than 2004, follow the link below to setup WSL for lower versions:
https://docs.microsoft.com/en-us/windows/wsl/install-manual

Install Solana Program Library:

Once you have setted up everything, we have to install solana program library. We can do that by writing the following command on ubuntu terminal:

cargo install spl-token-cli

Creating Your Own wallet and check on Solana Explorer:

After solana program library is installed, we have to create a wallet that can store some money. To do that, write the following command on terminal and just press enter on the passphrase:

solana-keygen new

If you already possess it then write it with --force at the end. It will create a new One.

This will create a wallet with our public key. To view the public key, write:

solana-keygen pubkey

To check the balance of the wallet, you will write:

solana balance --url devnet

The output will be zero as we havent added anything in our wallet.

To verify the balance, you can also check it on solana explorer. Copy and paste the pub key and go to explorer.solana.com.Switch to devnet in settings and paste the pub key on search box and you will see the balance is zero. 

Airdrop Money in Wallet:To airdrop money in wallet, go to terminal and write:

solana airdrop 2 pub_key --url devnet

If you check the balance, it will be increased to 2 SOL.

Creating a Token:

We are now going to create a token with the spl library of Solana. It is called SPL token program which creates tokens. We can create a token by writing:

spl-token create-token --url devnet

It will create a token. It will display a address through which you can access that token. So be sure to copy it and save it somewhere

Minting Your Token:

Now creating a token basically means to define the structure of the token. But Minting means to make copies of that specific token. Now have to create an account for that token. So we can create an account by:

spl-token create-account token_address --url devnet

You will give the same token address that you saved here.This will give the account address.Save it somewhere for now. Now that the account has been created, we can check the balance by:

spl-token balance token_address --url devnet

It will return 0 balance as we havent added any tokens in this account. Now to increase our tokens which is minting. We can do the minting process by:

spl-token mint token_address no._of_tokens --url devnet

This will add tokens into your account. You can check the balance of the account and it will be the amount you have specified.

Limit the total supply of your token and burn your token:

We can check how many tokens we minted and how many tokens people are using on the blockchain. We can check the circulating supply of the tokens which are the total numbers of the tokens being used by solana users by:

spl-token supply token_address --url devnet

The output will be same as the amount of tokens you entered. Now Solana possesses a command of authority. You can also renounce your authority from minting and once done you cannot mint forever. You can do this by:

spl-token authorize token_address mint --disable --url devnet

This will disable your authoity to mint. So you cannot mint even once now.If you try to mint, it will give error. Now if you want to burn a token or you can say remove your token from your account. You will use the account_adress you saved earlier. You can do this buy:

spl-token burn account_address no._of_tokens --url devnet

Note that you can burn tokens from only your own account and not from others.

Send your tokens to your friends with the Solana Wallet:

Lets say you want to mint tokens to your friends. To send some tokens to your friends, they will need to have a wallet of themselves. First go to sollet.io. Create a wallet there. It will ask you to save your key and enter password. After wallet has been created, change the network from mainnet to devnet. Then you have to add some SOL into the account. So in order to do that copy the address of the account and go to terminal and write:

solana airdrop 2 address --url devnet

And now refresh the page and you will see that you have added 2 SOL in the wallet. Now click on plus sign and goto manual input and write your own token_address in the mint_address tab. Next you can give any name and symbol your friend desires. And click on add token. And it will show on the main screen. Now in order to send money to that account, copy the address and write:

spl-token transfer token_address no._of_tokens friend_address --url devnet

This will transfer the number of tokens you have entered into his account.
