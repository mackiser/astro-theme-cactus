---
title: "Generating login information with Python"
publishDate: "21 May 2024"
description: "a simple python script to create user credentials based on the user's input"
tags: ["python"]
---

## Goal
Given the user's first and last name, write a Python script that generates a username, email address, 5-digit employee ID number and temporary password.


## Import necessary modules

Start by importing the built in `string` and `random` modules

```python
import string
from random import choice, shuffle
```

## Define a create_user function

We will define our first function called `create_user` with the parameters of first_name, last_name and phone_number.

Next we will define our `username` variable by taking the first letter of the user's first name, converting it to lowercase, and appending it to their last name (also in lower case).

Create a new variable called `email` and set it to the `username` appended with 'company.com' at the end.

Finally, we will print a welcome message, their username, email address and phone number in the terminal.

```python
def create_user(first_name, last_name, phone_number):
    first_name = first_name
    last_name = last_name
    phone_number = phone_number

    username = first_name[0].lower() + last_name.lower()
    email = username + "@company.com"

    print(f"\nGreetings {first_name}!")
    print(f"Username: {username}")
    print(f"Email Address: {email}")
    print(f"Phone Number: {phone_number}")
```

## Define a create_employee_id function

Create a function that generates a random 5-digit employee ID number.

First we will start by defining the digits that are available to use by using the `string` module. Then we will shuffle that list of numbers.

Create an empty string called `employee_id` and then write a for loop to append a random digit to the string until we get to 5 characters.

Then print the result!

```python
def create_employee_id():
    digits = list(string.digits)
    shuffle(digits)
    employee_id = ""
    for i in range(5):
        employee_id += choice(digits)
    print(f"Employee ID: {employee_id}")
```

## Define a create_random_pass function

This is essentially the same as the `create_employee_id` function but with a password length parameter and more characters instead of just integers.

We will define the lowercase and uppercase letters and the digits in the beginning. Then we will combine those lists into one list called `all_chars`.

Then we will shuffle `all_chars` and write a for loop appending a random character to the password until we reach our password length that was provided when we eventually call the function.

Lastly, we will print the password in the terminal.

```python
def create_random_pass(length):
    lower_case = list(string.ascii_lowercase)
    upper_case = list(string.ascii_uppercase)
    digits = list(string.digits)

    all_chars = lower_case + upper_case + digits
    shuffle(all_chars)

    length = length
    password = ""

    for i in range(length):
        password += choice(all_chars)
    print(f"Temporary Password: {password}")
```

## Obtaining user information

We will ask the user their first name, last name and phone number as strings and then pass those variables through when we call the `create_user` function.

```python
print("Welcome to Sample Company enrollment! \n")
first_name = input("First Name: ")
last_name = input("Last Name: ")
phone_number = input("Phone Number: ")
```

## Calling the functions

Finally we will call all of the functions we defined above and generate the login information!

```python
create_user(first_name, last_name, phone_number)
create_employee_id()
create_random_pass(10)
```

## Output

If done correctly the result should look something like this:

```r
Welcome to Sample Company enrollment!

First Name: Lamar
Last Name: Jackson
Phone Number: 555-555-5555

Greetings Lamar!
Username: ljackson
Email Address: ljackson@company.com
Phone Number: 555-555-5555
Employee ID: 94312
Temporary Password: QuHMWDRJJt
```