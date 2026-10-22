# DelugeScript – Zoho CRM Automation

A collection of Deluge custom functions developed to automate common tasks in Zoho CRM, especially Contact management, record creation and updates, age calculation, discount calculation, and REST API integration.

## 📌 Project Overview

This project demonstrates how Zoho Deluge can be used to automate CRM operations, work with record data, integrate external APIs, and update Contact records dynamically.

### Key Features

- Create Contact records using dynamic input parameters.
- Associate an Account with an existing Contact.
- Calculate age from the Contact's date of birth.
- Calculate the final amount after applying a discount.
- Fetch user data from an external REST API.
- Create Contacts using API response data.
- Send Contact information to an external API using POST.
- Update secondary email and mobile fields automatically.

## 🛠️ Technologies Used

- **Zoho CRM** – Contact records and CRM operations
- **Deluge** – Custom functions and automation logic
- **REST API** – HTTP GET and POST requests
- **JSON** – API response data handling
- **DummyJSON API** – Sample external user data

## 📂 Project Scripts

### 1. Accounts_Add_in_Contact.deluge

**Purpose:** Associate an existing Account with a Contact.

**Functionality:**
- Accepts a Contact ID and an Account ID.
- Creates a map containing the Account lookup ID.
- Updates the Contact's `Account_Name` field.
- Displays the update response.

**Function parameters:** `contactId`, `accountId`

### 2. After_Discount_Calculate.deluge

**Purpose:** Calculate the amount payable after applying a percentage discount.

**Formula:**

`Final Amount = Amount - (Amount × Discount / 100)`

**Functionality:**
- Fetches the Contact record using its ID.
- Reads `Currency_Amount` and `Discount`.
- Handles empty values using `ifnull()`.
- Calculates the discounted amount.
- Updates the `After_Discount_Amount` field.

**Function parameter:** `contactId`

### 3. Api_Create_Contact.deluge

**Purpose:** Create a Contact using data retrieved from an external API.

**API endpoint:** `https://dummyjson.com/users?limit=1`

**Functionality:**
- Sends a GET request to DummyJSON.
- Retrieves the first user from the response.
- Checks whether a Contact with the same email already exists.
- Maps first name, last name, email, phone, and date of birth.
- Creates a Contact only when a matching email is not found.

**Key concept:** API integration with duplicate checking.

### 4. Api_Get_Example.deluge

**Purpose:** Retrieve external user data and create a Contact in Zoho CRM.

**API endpoint:** `https://dummyjson.com/users`

**Functionality:**
- Fetches a list of users using a GET request.
- Selects a user from the API response.
- Maps the user's details to Contact fields.
- Converts the date of birth into `yyyy-MM-dd` format.
- Creates a Contact and requests workflow triggering.

**Key concept:** GET requests, response handling, field mapping, and CRM record creation.

### 5. Calculate_Age.deluge

**Purpose:** Calculate a Contact's age using the date of birth.

**Functionality:**
- Fetches the Contact record.
- Reads the `Date_of_Birth` field.
- Calculates the difference between the current year and birth year.
- Checks whether the birthday has occurred this year.
- Reduces the calculated age by one if the birthday is still upcoming.
- Updates the Contact's `AGE` field.

**Function parameter:** `contactId`

### 6. Create_Contact.deluge

**Purpose:** Create a Contact using dynamically supplied input parameters.

**Functionality:**
- Accepts first name, last name, department, email, and phone.
- Stores the values in a Deluge map.
- Creates a Contact in Zoho CRM.
- Requests workflow triggering during record creation.

**Function parameters:** `first_name`, `Last_Name`, `department`, `email`, `phone`

**Key concept:** Dynamic input parameters and CRM record creation.

### 7. Send_Contact_Post.deluge

**Purpose:** Send Contact information from Zoho CRM to an external REST API.

**API endpoint:** `https://dummyjson.com/users/add`

**Functionality:**
- Fetches a Contact using its ID.
- Extracts the first name, last name, email, and phone.
- Prepares the request body and JSON content-type header.
- Sends a POST request to the API.
- Displays the API response.

**Function parameter:** `contactId`

### 8. Update_Contact.deluge

**Purpose:** Copy existing Contact information into other fields.

**Functionality:**
- Fetches a Contact using its ID.
- Reads the email and phone fields.
- Copies email to `Secondary_Email` when populated.
- Copies phone to `Mobile` when populated.
- Updates the record only if there are values to update.

**Function parameter:** `contactId`

## 🔄 How the Project Works

1. Receive input parameters or fetch data from an external API.
2. Retrieve or prepare the required Contact information.
3. Map values to Zoho CRM field API names.
4. Create or update the CRM record.
5. Display the response for verification.

## ⚙️ Setup and Usage

1. Open your Zoho CRM organization.
2. Navigate to the Functions section.
3. Create a custom function or open an existing function.
4. Copy the corresponding Deluge script into the editor.
5. Configure the function arguments and any required workflow or button.
6. Verify that the Contact and Account field API names match your CRM configuration.
7. Save and test the function with valid record IDs and sample data.

## 🔐 Important Notes

- The scripts are examples and may require adjustments for your Zoho CRM configuration.
- Field API names such as `Currency_Amount`, `Discount`, `After_Discount_Amount`, `Date_of_Birth`, `AGE`, and `Secondary_Email` must exist in your CRM.
- The Account lookup field must use the correct API name and record ID.
- DummyJSON is a sample API; its responses are intended for demonstration, not permanent data storage.
- Test record creation and update functions in a development environment before using them in production.
- Validate API responses and handle errors appropriately before relying on these functions in a live workflow.

## 🎯 Learning Outcomes

This project demonstrates practical experience with:

- Deluge syntax and functions
- Maps and data manipulation
- Zoho CRM record creation, retrieval, and updates
- REST API integration using GET and POST
- JSON response handling
- Duplicate record checking
- Date conversion and age calculation
- Conditional logic and null-value handling
- CRM field mapping and workflow triggering

## 👨‍💻 Author

**Sandeep Mehra**

GitHub: [@sandeepmehra28](https://github.com/sandeepmehra28)

---

This repository is maintained as a practical learning project for Zoho CRM Deluge scripting and API integration.
