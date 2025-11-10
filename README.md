# Simple User API

## 1. Program Overview

This project implements a simple API with GET and POST Functionality. It allows the user get the list of users The aim of this project to be able to learn how to create APIs and test them using Postman.

## 2. Source Codes
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

## 3. Testing

**Testing this project will require that you have a local web server such as XAMPP as well as an all-in-one API platform like Postman installed.**

### 1. GET
#### Steps
##### 1.
##### 2.
##### 3.
##### 4.
##### 5.


### 2. POST
#### Steps
##### 1.
##### 2.
##### 3.
##### 4.
##### 5.

### Step 3: Implementing the `Order` Class
#### Steps
##### 1.
##### 2.
##### 3.
##### 4.
##### 5.

## 4. Members
**This project is a collaborative project between Drennix Jean-Roe E. Guerrero and John Dale Guiang as Team GG for CS0053 TN37**

### Sample Test Run


