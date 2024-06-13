# #MyToken Solidity Contract
Overview
MyToken is a basic Ethereum token contract. It allows you to create (mint) and destroy (burn) tokens, keeping track of the total supply and balances of each address.

Features
Token Name: NewToken
Token Abbreviation: NTK
Total Supply: Tracks the total number of tokens in existence.
Balances: Tracks the number of tokens each address holds.

Functions
'mint'
function mint(address _address, uint _value) public

Increases the total supply by "_value".
Adds _value tokens to the balance of "_address".

'burn'
function burn(address _address, uint _value) public

Decreases the total supply by "_value".
Removes _value tokens from the balance of "_address" (if the balance is sufficient).

Usage
Mint Tokens:

Call mint with the recipient's address and the amount of tokens to create.
Example: mint(0x5B38Da6a701c568545dCfcB03FcB875f56beddC4, 1000)
Burn Tokens:

Call burn with the address and the amount of tokens to destroy.
Example: burn(0x5B38Da6a701c568545dCfcB03FcB875f56beddC4, 500)

Example Code



 // SPDX-License-Identifier: MIT

pragma solidity 0.8.18;


contract MyToken {

    // Public variables to store the details about the coin
    string public tokenName = "NewToken";
    string public tokenAbbrv = "NTK";
    uint public totalSupply=0;

    // Mapping to store balances of addressess
    mapping(address => uint) public balances;

    // Mint function to increase the total supply and balance of a given address
    function mint (address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // Burn function to decrease the total supply and balance of a given address
    function burn (address _address, uint _value) public {
        if (balances[_address] >= _value) {
            totalSupply -= _value;
            balances[_address] -= _value;
        }
    }
}

