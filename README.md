File name - scholarchain
link - https://repo.sourcify.dev/11142220/0xae32dfC9F60E5BBED0f0885113ECd567b58407fa/
image url - ![15F3E9BF-C803-4FCC-AB4E-2E8815903759](https://github.com/user-attachments/assets/645a0b73-0267-4822-ab1f-e913374e2d02)


# 🧾 Student Record Smart Contract

## 📘 Overview

The **Student Record** smart contract provides a transparent and tamper-proof way to record and verify student achievements on the blockchain.

Each student (identified by their Ethereum address) can add achievements — such as course completions, certifications, or awards — to their personal record.
These achievements are stored permanently on-chain and can be retrieved or verified by anyone.


## ⚙️ Features

✅ **Add Achievements:**
Students can record new achievements, such as course completions or certificates, by providing a title and description.

✅ **View Achievements:**
Anyone can view all the achievements of a student by entering their Ethereum address.

✅ **Count Achievements:**
You can also check how many total achievements a student has recorded.

✅ **Event Logging:**
Every new achievement emits an event that can be tracked off-chain (for example, in DApps or web applications).


## 🧱 Smart Contract Structure

### 1. `struct Achievement`

Stores information about a single achievement:

* `title` → Name of the course or certification (e.g., *"Blockchain Fundamentals"*)
* `description` → Short detail about it (e.g., *"Scored 95% in final exam"*)
* `date` → Timestamp when the achievement was recorded

---

### 2. `mapping(address => Achievement[]) studentAchievements`

This mapping links each student’s Ethereum address to an array (list) of their achievements.

---

### 3. `event AchievementAdded`

This event is emitted whenever a new achievement is added.
It helps external applications detect updates on the blockchain.

---

### 4. `function addAchievement(string _title, string _description)`

Allows a student to add a new achievement to their record.
**Parameters:**

* `_title`: The name of the course or achievement
* `_description`: A short summary or detail of the achievement

Once added, the achievement is:

* Stored in the student's record
* Logged via the `AchievementAdded` event

---

### 5. `function getAchievements(address _student)`

Returns all achievements of a given student address.
**Usage Example:**
Retrieve and display all achievements for verification.

---

### 6. `function getAchievementCount(address _student)`

Returns the total number of achievements recorded by the given student.

---

## 💻 Example Usage

### 1. Add an Achievement

```solidity
addAchievement("Completed Blockchain Course", "Scored 95% in Blockchain Fundamentals");
```

### 2. Retrieve All Achievements

```solidity
getAchievements(0x1234...ABCD); // Returns all achievements for that student address
```

### 3. Count Total Achievements

```solidity
getAchievementCount(0x1234...ABCD); // Returns total number of achievements
```

---

## 🔒 Security Notes

* Only the student (message sender) can add achievements to **their own** record.
* Once recorded, achievements are stored **permanently** on the blockchain and cannot be deleted or altered.
* All data is publicly readable to ensure transparency and verifiability.

---

## 🧠 Possible Extensions

You can improve this contract by:

* Adding **admin or institution verification** (so only verified schools can add records).
* Including **metadata URIs** (e.g., IPFS links to certificates).
* Integrating **soulbound tokens (SBTs)** to make achievements tokenized and non-transferable.

Acknowledgments
Celo Blockchain for providing eco-friendly infrastructure
Remix IDE for easy smart contract testing
Blockscout for transparent transaction viewing    
