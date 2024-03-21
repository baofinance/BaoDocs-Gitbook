# Private keys & .env file

Foundry supports encrypted private keys

Basically you use cast to password-encrypt the key

$ cast wallet import \<name-for-key> --interactive

this will ask for:&#x20;

* your private key - this should be the last time you see your private key again in plain text!
* a password - yes you have to remember the password, and the address returned so not completely secure.

and return an address (to be used later)

You could save the password in a .password file and add .password to the .gitignore file.

Use

$ cast wallet list

or

$ ls \~/.foundry/keystores/

to show all the wallet names you have encrypted the private keys for. The files in the \~/.foundry/keystores/ directory are ERC-2335 encrypted keystores

so now instead of using --private-key \<your-private-key>

use --account \<name-for-key> --sender \<address-returned-by-cast-wallet-import>

e.g:

$ forge script script/\<script-name>:\<script-function> --rpc-url \<whatever> --account \<name-for-key> --sender \<address-returned-by-cast-wallet-import> \<etc...>

For more info see [https://www.youtube.com/watch?v=VQe7cIpaE54](https://www.youtube.com/watch?v=VQe7cIpaE54)
