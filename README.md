# Errors Handling and functions

This Solidity program is a simple "Error handling" program that demonstrates the basic error and functionality concepts of the Solidity programming language.

## Description

This program is  contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has a three functions that returns the different outputs. This program serves as a simple and straightforward introduction to Error handling and functions concept in Solidity programming, and can be used as a stepping stone for more complex projects in the future.

## Getting Started

### Executing program

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ErrorHandling {
    uint public X;

    function setValue(uint value) public {
        require(value > 0, "Value must be greater than zero");
        X = value;
    }
    function checkValue() public view {
        if (X %2 != 0) {
            revert("Value is odd number ");
        }
    }
    function testingValue() public view {
       assert(X > 0);
    }
}

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.0" (or another compatible version), and then click on the "Compile Error handling.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "ErrorHandling" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling all the functions that are "setValue", "checkValue" and "testingValue". Click on the "ErrorHandling" contract in the left-hand sidebar, and then click on the  "setValue", "checkValue" and "testingValue" functions. Finally, click on the "transact" button to execute the function and retrieve the output.

## Authors

Muskan sharma @Muskan5972


## License

This project is licensed under the MIT License.
