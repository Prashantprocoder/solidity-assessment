# solidity-assessment 
This Solidity program is a simple "TOKEN" program that demonstrates the basic syntax and functionality of the Solidity programming language.
DESCRIPTION:-
The 'MY TOKEN' contract is a simple implementation of a custom ERC-20-like token on the Ethereum blockchain. It defines a token named 
"PRASHANT" with the abbreviation "PRA" and provides basic functionalities to mint and burn tokens.
Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.




// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // public variables here
    string public tokenName = "PRASHANT";
    string public tokenAbbrv = "PRA";
    uint public totalSupply = 10;

    // mapping variable here
     mapping (address => uint)public balances;

    // mint function
    function mint(address _address, uint _value) public {
      totalSupply += _value;
      balances[_address] += _value;
    }   
  
    // burn function
    function burn (address _address,uint _value) public {
       require(balances [_address ] >= _value ,"insufficient balance to burn");{
        totalSupply -= _value;
        balances[_address] -= _value;
      }
    }

}
