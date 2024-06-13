# MyBankTransactions
This solidity program is used to depositing, getting, transfering ethers. The main purpose of this program is to understand the usage of revert(), assert() and require() function whose are basically the part of error handling.

## Description
Solidity programming language is used to write this program. Solidity is mostly used to build smart contracts. In this program we have created a smart contract named as MyBank. In this contract firstly I have created a mapping variable which maps an address to a unsigned integer value which is basically indicating the amount of ether in the account it is mapped with. After that we have created four functions for different purposes. First function is used to depositting some amount of token in the account of the sender, in this function we have used require() function to maintain the integrity. Second function is basically used to transfer a certain amount of ether to a particular user from the account of sender, in this we have used three revert() functions to revert the specified message when different conditions met. Third function is generally to get the current balance of sender. The last function is used to check or understand the use assert() function.

## Getting Started

### Executing Program
To execute this program you can go to the Remix IDE which is open IDE for Solidity. For that you can click on this link https://remix.ethereum.org/

Once you successfully reached to the IDE create a new file by clicking on the '+' icon and saving that file with .sol extension (e.g. MyBank.sol). After this copy and paste the code in your file that is given below 

```javascript
// SPDX-License-Identifier: MIT
pragma solidity 0.8.24;

contract Assesment3 {
    mapping(address => uint256) private balances;
    function deposit() public payable {
        require(msg.value > 0, "Amount must be greater than 0");        
        balances[msg.sender] += msg.value;
    }
    function transfer(address user, uint256 amount) public{
        if(amount <= 0){
            revert("Amount must be greater than zero");
        }
        else if (balances[msg.sender] < amount){
            revert("Not enough tokens to send");
        }
        else if (amount > 100) {
            revert("Cannot send more than 100 ethers at a time");
        }
        else{
            balances[msg.sender] -= amount;
            balances[user] += amount;
        }
    }
    function getBalance() public view returns (uint256) {
        return balances[msg.sender];
    }
    function testAssert() public view {
        assert(!(balances[msg.sender] < 0));
        //assert(balances[msg.sender] != 0);
    }
}

```

After pasting this code you have to compile the code from the left hand sidebar. click on the 'Solidity Compiler' then click on the 'Compile MyBank.sol' button.

After the successful compilation of the code you have to deploy the program. For that you have again another option on the left sidebar that is 'Deploy & Run Transactions' and then you will see a deploy button; before clicking on it make sure that the file showing there is 'MyBank.sol'. Then you will be able to see the file in the 'Deployed/Unpinned Contracts' click on that now all the public variable and functions are visible to you now execute and fetch the values according to you.


## Authors
Abhishek

## License
This project is licensed under the MIT License.
