File name - scholarchain
link - https://repo.sourcify.dev/11142220/0xae32dfC9F60E5BBED0f0885113ECd567b58407fa/
image url - ![15F3E9BF-C803-4FCC-AB4E-2E8815903759](https://github.com/user-attachments/assets/645a0b73-0267-4822-ab1f-e913374e2d02)

d
    /// @param _title The name of the course or achievement
    /// @param _description A short description of the achievement
    function addAchievement(string memory _title, string memory _description) public {
        // Create a new achievement
        Achievement memory newAchievement = Achievement({// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

/// @title Student Record - Verifiable record of student achievements
/// @author 
/// @notice This contract allows storing and verifying student achievements on-chain
contract StudentRecord {

    // Structure to store a student's achievement
    struct Achievement {
        string title;         // e.g., "Completed Blockchain Course"
        string description;   // e.g., "Scored 95% in Blockchain Fundamentals"
        uint256 date;         // Timestamp of when the achievement was added
    }

    // Mapping of student address to their list of achievements
    mapping(address => Achievement[]) private studentAchievements;

    // Event emitted whenever a new achievement is added
    event AchievementAdded(
        address indexed student,
        string title,
        string description,
        uint256 date
    );

    /// @notice Add a new achievement to your student recor
            title: _title,
            description: _description,
            date: block.timestamp
        });

        // Store the achievement in the sender's record
        studentAchievements[msg.sender].push(newAchievement);

        // Emit an event for verification
        emit AchievementAdded(msg.sender, _title, _description, block.timestamp);
    }

    /// @notice Retrieve all achievements of a student
    /// @param _student The Ethereum address of the student
    /// @return An array of Achievement structs
    function getAchievements(address _student) public view returns (Achievement[] memory) {
        return studentAchievements[_student];
    }

    /// @notice Get the total number of achievements for a student
    /// @param _student The Ethereum address of the student
    /// @return count The number of recorded achievements
    function getAchievementCount(address _student) public view returns (uint256 count) {
        return studentAchievements[_student].length;
    }
}

