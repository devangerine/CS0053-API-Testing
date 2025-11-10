# Simple User API and Testing using Postman

## 1. Program Overview

This project implements a simple API with GET and POST Functionality. It allows the user get the list of users The aim of this project to be able to learn how to create APIs and test them using Postman.

## 2. Tools Used
This project was implemented using the following:
| Component | Specification |
| :--- | :--- |
| **Programming Language** | PHP 8.2.12 and Javascript ECMAScript 2025 |
| **Development Environment** | Visual Studio Code 1.105 |
| **Local Webserver** | XAMPP |
| **API Platform** | Postman |



## 3. Source Codes
### API
```
<?php
header("Content-Type: application/json");

$users = [
    ["id" => 1, "name" => "Alice"],
    ["id" => 2, "name" => "Bob"],
];

if ($_SERVER['REQUEST_METHOD'] === 'GET') {
    echo json_encode($users);
} elseif ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $data = json_decode(file_get_contents("php://input"), true);
    $newUser = [
        "id" => count($users) + 1,
        "name" => $data['name']
    ];
    $users[] = $newUser;
    echo json_encode($newUser);
}
?>
```
### Test Script
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response is JSON", function () {
    pm.response.to.be.json;
});
```

## 4. Testing

**Testing this project will require that you have a local web server such as XAMPP as well as an all-in-one API platform like Postman installed.**

### Preparation 
#### Steps
 1. Paste a copy of the API source code file into the ```htdocs``` subdirectory of XAMPP which can be found with this file path or wherever you installed XAMPP: ```C:\xampp\htdocs```
 2. Open XAMPP.
 3. Click the start button found to the right of the Apache module.
 4. Open Postman.
 5. Go to the collections tab found in around the top left corner of the Postman window.
 6. Click the ```+``` button to the right of the Collections tab and click Blank collection. Rename that collection to whatever you deem fit as this will serve as our testing ground for this project.
 ![Postman Create Collection screenshot](https://github.com/devangerine/CS0053-API-Testing/blob/main/Screenshots/Postman%20Creating%20a%20Collection.png)

### 1. Testing GET request
#### Steps
 1. Open Postman if not already open.
 2. Make sure you are using the GET method otherwise click the dropdown and select GET before proceeding.
 3. Paste the following URL in the provided field in postman: ```http://localhost/api.php```
 4. Click Send.
 5. Check the results found in the window below. It should return the list of users along with their respective id numbers.
 ![GET Request Test - Result screenshot](https://github.com/devangerine/CS0053-API-Testing/blob/main/Screenshots/Get%20Request%20-%20Result.png)


### 2. Testing POST request
#### Steps
 1. Open Postman if not already open.
 2. Make sure you are using the POST method otherwise click the dropdown and select POST before proceeding.
 3. Paste the following URL in the provided field in postman: ```http://localhost/api.php```
 4. Navigate to the Body tab found under the url input field.
 5. Click the drop down below Params and select the ```raw``` format.
 6. Paste the following code in the input field provided below: ```raw```: ```{ "name": "Charlie" }```
 7. Click Send.
 8. Check the results found in the window below. It should return the name and id of the user you have just added.
 ![POST Request Test - Result screenshot](https://github.com/devangerine/CS0053-API-Testing/blob/main/Screenshots/Push%20Request%20-%20Result.png)

### 3. Postman Tests
#### Steps
 1. Open Postman if not already open.
 2. Make sure you are using the POST method otherwise click the dropdown and select POST before proceeding.
 3. Paste the following URL in the provided field in postman: ```http://localhost/api.php```
 4. Make sure you have not cleared the code you have pasted in the body tab before proceeding. If you have just paste it there again.
 5. Navigate to the Body tab found under the url input field.
 6. Navigate to the Scripts tab founder under the url input field.
 7. Navigate to the ```Post-res``` tab and paste the following code in the code field beside it:
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response is JSON", function () {
    pm.response.to.be.json;
});
```
 8. Click Send.
 9. Check the test results found in the window below. It should return PASSED Status code is 200 for and PASSED Response is JSON.
 ![Postman Tests - Result screenshot](https://github.com/devangerine/CS0053-API-Testing/blob/main/Screenshots/Push%20Requests%20but%20with%20Postman%20Tests%20-%20Result.png)


## 5. Members
This project is a collaborative project between **Drennix Jean-Roe E. Guerrero** and **John Dale Guiang** as **Team GG** for CS0053 TN37


**Drennix Jean-Roe E. Guerrero** - Coding and Documentation


**John Dale Guiang** - Coding and Documentation



