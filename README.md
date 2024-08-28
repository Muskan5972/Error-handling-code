# Errors Handling and functions

This Solidity program is a simple "Error handling" program that demonstrates the basic error and functionality concepts of the Solidity programming language.

## Description

This program is  contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has a three functions that returns the different outputs. This program serves as a simple and straightforward introduction to Error handling and functions concept in Solidity programming, and can be used as a stepping stone for more complex projects in the future.

## Overview
The SchoolGradingSystem smart contract allows an owner (typically the admin) to register students, assign grades, update grades, and retrieve grades for students. The contract includes state variables, events, and several functions with essential Solidity features such as require, assert, and revert.

### Executing program
````
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SchoolGradingSystem {

    // State variables
    
    address public owner;
    
    mapping(address => uint) public studentGrades;
    
    mapping(address => bool) public registeredStudents;

    // Events
    event StudentRegistered(address indexed student);
    event GradeAssigned(address indexed student, uint grade);
    event GradeUpdated(address indexed student, uint newGrade);

    constructor() {
        owner = msg.sender;
    }

    // Modifier to check if the sender is the owner
    modifier onlyOwner() {
        require(msg.sender == owner, "Only owner can perform this action");
        _;
    }

    // Register a new student
    function registerStudent(address _student) public onlyOwner {
        require(!registeredStudents[_student], "Student is already registered");
        registeredStudents[_student] = true;
        emit StudentRegistered(_student);
    }

    // Assign a grade to a student
    function assignGrade(address _student, uint _grade) public onlyOwner {
        require(registeredStudents[_student], "Student is not registered");
        require(_grade >= 0 && _grade <= 100, "Grade must be between 0 and 100");
        studentGrades[_student] = _grade;
        emit GradeAssigned(_student, _grade);
    }

    // Update the grade of a student
    function updateGrade(address _student, uint _newGrade) public onlyOwner {
        require(registeredStudents[_student], "Student is not registered");
        require(_newGrade >= 0 && _newGrade <= 100, "Grade must be between 0 and 100");
        // Using revert to handle grade greater than 100
        if (_newGrade > 100) {
            revert("New grade cannot be greater than 100");
        }

        studentGrades[_student] = _newGrade;
        
        // Using assert to check if the grade is correctly updated
        assert(studentGrades[_student] == _newGrade);

        emit GradeUpdated(_student, _newGrade);
    }

    // View the grade of a student
    function getGrade(address _student) public view returns (uint) {
        require(registeredStudents[_student], "Student is not registered");
        return studentGrades[_student];
    }

}

`````

## Working
This project is a basic school grading system where the owner (like a school administrator) can register students, assign grades, and update those grades. The contract uses checks to make sure only valid actions are performed:

__Registering Students:__ The owner can add students to the system, ensuring that a student is not already registered.

__Assigning Grades:__ The owner can assign a grade between 0 and 100 to a registered student.

__Updating Grades:__ The owner can update a student’s grade but ensures the new grade is also between 0 and 100. If the grade is over 100, the function will stop and cancel the update.

## Authors

Muskan sharma @Muskan5972


## License

This project is licensed under the MIT License.
