# Errors Handling and functions

This Solidity program is a simple "Error handling" program that demonstrates the basic error and functionality concepts of the Solidity programming language.

## Description

This program is  contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has a three functions that returns the different outputs. This program serves as a simple and straightforward introduction to Error handling and functions concept in Solidity programming, and can be used as a stepping stone for more complex projects in the future.

## Getting Started

### Executing program
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ErrorDemonstration {
    uint public storedValue;

    // Event to log changes
    event ValueUpdated(uint newValue);

    // Function to set the value and demonstrate `require`
    function setValue(uint newValue) public {
        // `require` ensures that the value is positive
        require(newValue > 0, "Value must be greater than zero");
        storedValue = newValue;
        emit ValueUpdated(newValue);
    }

    // Function to demonstrate `revert` for custom error handling
    function checkEven() public view returns (string memory) {
        // `revert` is used to handle specific error conditions
        if (storedValue % 2 != 0) {
            revert("Stored value is not an even number");
        }
        return "Stored value is even";
    }

    // Function to demonstrate `assert` for internal consistency checks
    function validateState() public view {
        // `assert` checks that the stored value is non-negative
        assert(storedValue >= 0);
    }
}


To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.0" (or another compatible version), and then click on the "Compile Error handling.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Errordemostration" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling all the functions that are "setValue", "checkValue" and "testingValue". Click on the "ErrorHandling" contract in the left-hand sidebar, and then click on the  "setValue", "checkeven" and "validatestate" functions. Finally, click on the "transact" button to execute the function and retrieve the output.

## Authors

Muskan sharma @Muskan5972


## License

This project is licensed under the MIT License.
