 ![Image](https://camo.githubusercontent.com/a0c52a69dc410e983b8c63fa4aa57e83cb4157cd/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f696e7472616e65742d70726f6a656374732d66696c65732f686f6c626572746f6e7363686f6f6c2d6869676865722d6c6576656c5f70726f6772616d6d696e672b2f3236332f4842544e2d68626e622d46696e616c2e706e67) 
# Airbnb Clone - The Console

## Project Goals


### General Objectives

*   How to create a Python package
*   How to create a command interpreter in Python using the cmd module
*   What is Unit testing and how to implement it in a large project
*   How to serialize and deserialize a Class
*   How to write and read a JSON file
*   How to manage datetime
*   What is an UUID
*   What is *args and how to use it
*   What is **kwargs and how to use it
*   How to handle named arguments in a function

### Primary Objective

 This project focuses on the development of the console part
 of the Air bnb clone holberton project which consists of 7 stages.

* The Console
* HTML
* My SQL
* HTML with Fabric
* Flask web application server
* REST API
* WEB Dynamic

#### Functionalities of this command interpreter:
* Create a new object (ex: a new User or a new Place)
* Retrieve an object from a file, a database etc...
* Do operations on objects (count, compute stats, etc...)
* Update attributes of an object
* Destroy an object

## Table of Content
* [Environment](#environment)
* [Installation](#installation)
* [File Descriptions](#file-descriptions)
* [Usage](#usage)
* [Examples of use](#examples-of-use)
* [Bugs](#bugs)
* [Authors](#authors)
* [License](#license)

## Environment
This project is interpreted/tested on Ubuntu 14.04 LTS using python3 (version 3.4.3)

## Installation
* Clone this repository: `git clone "https://github.com/jemn21819/AirBnB_clone.git"`
* Access AirBnb directory: `cd AirBnB_clone`
* Run hbnb(interactively): `./console` and enter command
* Run hbnb(non-interactively): `echo "<command>" | ./console.py`

## File Descriptions
[console.py](console.py) - the console contains the entry point of the command interpreter. 
List of commands this console current supports:
* `EOF` - exits console 
* `quit` - exits console
* `<emptyline>` - overwrites default emptyline method and does nothing
* `create` - Creates a new instance of`BaseModel`, saves it (to the JSON file) and prints the id
* `destroy` - Deletes an instance based on the class name and id (save the change into the JSON file). 
* `show` - Prints the string representation of an instance based on the class name and id.
* `all` - Prints all string representation of all instances based or not on the class name. 
* `update` - Updates an instance based on the class name and id by adding or updating attribute (save the change into the JSON file). 

#### `models/` directory contains classes used for this project:
[base_model.py](/models/base_model.py) - The BaseModel class from which future classes will be derived
* `def __init__(self, *args, **kwargs)` - Initialization of the base model
* `def __str__(self)` - String representation of the BaseModel class
* `def save(self)` - Updates the attribute `updated_at` with the current datetime
* `def to_dict(self)` - returns a dictionary containing all keys/values of the instance

Classes inherited from Base Model:
* [amenity.py](/models/amenity.py)
* [city.py](/models/city.py)
* [place.py](/models/place.py)
* [review.py](/models/review.py)
* [state.py](/models/state.py)
* [user.py](/models/user.py)

#### `/models/engine` directory contains File Storage class that handles JASON serialization and deserialization :
[file_storage.py](/models/engine/file_storage.py) - serializes instances to a JSON file & deserializes back to instances
* `def all(self)` - returns the dictionary __objects
* `def new(self, obj)` - sets in __objects the obj with key <obj class name>.id
* `def save(self)` - serializes __objects to the JSON file (path: __file_path)
* ` def reload(self)` -  deserializes the JSON file to __objects

#### `/tests` directory contains all unit test cases for this project:
[/test_models/test_base_model.py](/tests/test_models/test_base_model.py) - Contains the TestBaseModel and TestBaseModelDocs classes
TestBaseModelDocs class:
* `def setUpClass(cls)`- Set up for the doc tests
* `def test_pep8_conformance_base_model(self)` - Test that models/base_model.py conforms to PEP8
* `def test_pep8_conformance_test_base_model(self)` - Test that tests/test_models/test_base_model.py conforms to PEP8
* `def test_bm_module_docstring(self)` - Test for the base_model.py module docstring
* `def test_bm_class_docstring(self)` - Test for the BaseModel class docstring
* `def test_bm_func_docstrings(self)` - Test for the presence of docstrings in BaseModel methods

TestBaseModel class:
* `def test_is_base_model(self)` - Test that the instatiation of a BaseModel works
* `def test_created_at_instantiation(self)` - Test created_at is a pub. instance attribute of type datetime
* `def test_updated_at_instantiation(self)` - Test updated_at is a pub. instance attribute of type datetime
* `def test_diff_datetime_objs(self)` - Test that two BaseModel instances have different datetime objects

[/test_models/test_amenity.py](/tests/test_models/test_amenity.py) - Contains the TestAmenityDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_amenity(self)` - Test that models/amenity.py conforms to PEP8
* `def test_pep8_conformance_test_amenity(self)` - Test that tests/test_models/test_amenity.py conforms to PEP8
* `def test_amenity_module_docstring(self)` - Test for the amenity.py module docstring
* `def test_amenity_class_docstring(self)` - Test for the Amenity class docstring

[/test_models/test_city.py](/tests/test_models/test_city.py) - Contains the TestCityDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_city(self)` - Test that models/city.py conforms to PEP8
* `def test_pep8_conformance_test_city(self)` - Test that tests/test_models/test_city.py conforms to PEP8
* `def test_city_module_docstring(self)` - Test for the city.py module docstring
* `def test_city_class_docstring(self)` - Test for the City class docstring

[/test_models/test_file_storage.py](/tests/test_models/test_file_storage.py) - Contains the TestFileStorageDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_file_storage(self)` - Test that models/file_storage.py conforms to PEP8
* `def test_pep8_conformance_test_file_storage(self)` - Test that tests/test_models/test_file_storage.py conforms to PEP8
* `def test_file_storage_module_docstring(self)` - Test for the file_storage.py module docstring
* `def test_file_storage_class_docstring(self)` - Test for the FileStorage class docstring

[/test_models/test_place.py](/tests/test_models/test_place.py) - Contains the TestPlaceDoc class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_place(self)` - Test that models/place.py conforms to PEP8.
* `def test_pep8_conformance_test_place(self)` - Test that tests/test_models/test_place.py conforms to PEP8.
* `def test_place_module_docstring(self)` - Test for the place.py module docstring
* `def test_place_class_docstring(self)` - Test for the Place class docstring

[/test_models/test_review.py](/tests/test_models/test_review.py) - Contains the TestReviewDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_review(self)` - Test that models/review.py conforms to PEP8
* `def test_pep8_conformance_test_review(self)` - Test that tests/test_models/test_review.py conforms to PEP8
* `def test_review_module_docstring(self)` - Test for the review.py module docstring
* `def test_review_class_docstring(self)` - Test for the Review class docstring

[/test_models/state.py](/tests/test_models/test_state.py) - Contains the TestStateDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_state(self)` - Test that models/state.py conforms to PEP8
* `def test_pep8_conformance_test_state(self)` - Test that tests/test_models/test_state.py conforms to PEP8
* `def test_state_module_docstring(self)` - Test for the state.py module docstring
* `def test_state_class_docstring(self)` - Test for the State class docstring

[/test_models/user.py](/tests/test_models/test_user.py) - Contains the TestUserDocs class:
* `def setUpClass(cls)` - Set up for the doc tests
* `def test_pep8_conformance_user(self)` - Test that models/user.py conforms to PEP8
* `def test_pep8_conformance_test_user(self)` - Test that tests/test_models/test_user.py conforms to PEP8
* `def test_user_module_docstring(self)` - Test for the user.py module docstring
* `def test_user_class_docstring(self)` - Test for the User class docstring

## How to use the console

The purpose of the console is to be able to create, show, destroy, save, and update all the classes we need/want. It allows us to start and stop processes when we need to. In other words, we can experiment with the file storage to test what we want and don't want. With our console.py file, here is a short guide on how to use our console:

```
AirBnB_clone$ ./console.py
(hbnb) 
(hbnb) 
(hbnb) all
[]
```

To run our console, simply type in "./console.py". The console will then prompt you with "(hbnb)". If you type all without creating a BaseModel (new class), empty brackets should print to the terminal. However, if class names and instances don't exist, errors should always print out. See example below:

```
(hbnb) all Basemodel
** class doesn't exist **
(hbnb) show BaseModel
** instance id missing **
(hbnb) show BaseModel 121212
** no instance found **
```

To create a new User:

```
(hbnb) User.create()
1bab8a19-a0c7-43ef-956b-b3271bdd684f
(hbnb) User.all()
["[User] (1bab8a19-a0c7-43ef-956b-b3271bdd684f) {'updated_at': datetime.datetime(2017, 10, 4, 18, 21, 27, 164392), 'email': '', 'created_at': datetime.datetime(2017, 10, 4, 18, 21, 27, 164366), 'last_name': '', 'password': '', 'id': '1bab8a19-a0c7-43ef-956b-b3271bdd684f', 'first_name': ''}"]
```

The above example is an advanced feature that allows you to create a new User using ".create". However, you can also create a new User with the regular syntax. For example:

```
(hbnb) create User
777f8007-5aeb-4568-8334-807d507edce0
(hbnb) all User
["[User] (777f8007-5aeb-4568-8334-807d507edce0) {'updated_at': datetime.datetime(2017, 10, 4, 18, 21, 59, 114711), 'email': '', 'created_at': datetime.datetime(2017, 10, 4, 18, 21, 59, 114685), 'last_name': '', 'password': '', 'id': '777f8007-5aeb-4568-8334-807d507edce0', 'first_name': ''}", "[User] (1bab8a19-a0c7-43ef-956b-b3271bdd684f) {'updated_at': datetime.datetime(2017, 10, 4, 18, 21, 27, 164392), 'email': '', 'created_at': datetime.datetime(2017, 10, 4, 18, 21, 27, 164366), 'last_name': '', 'password': '', 'id': '1bab8a19-a0c7-43ef-956b-b3271bdd684f', 'first_name': ''}"]
```

To show a specific User, you'll have to use the "show" command. The show command takes in two arguments - name and id. In the examples, User is the name of all users, but their ids are unique. Please see example below:

```
(hbnb) show User 777f8007-5aeb-4568-8334-807d507edce0
[User] (777f8007-5aeb-4568-8334-807d507edce0) {'updated_at': datetime.datetime(2017, 10, 4, 18, 21, 59, 114711), 'email': '', 'created_at': datetime.datetime(2017, 10, 4, 18, 21, 59, 114685), 'last_name': '', 'password': '', 'id': '777f8007-5aeb-4568-8334-807d507edce0', 'first_name': ''}
```

To destroy a User, use the "destroy" command. The command takes in two arguments - name and id. When successfully implemented, destroy will delete the User from file storage. Please see example below:

```
(hbnb) create User
06505348-0c86-4273-b1c2-68eefcbbab0c
(hbnb) show User 06505348-0c86-4273-b1c2-68eefcbbab0c
[User] (06505348-0c86-4273-b1c2-68eefcbbab0c) {'id': '06505348-0c86-4273-b1c2-68eefcbbab0c', 'last_name': '', 'updated_at': datetime.datetime(2017, 10, 4, 19, 18, 40, 976205), 'email': '', 'created_at': datetime.datetime(2017, 10, 4, 19, 18, 40, 976174), 'password': '', 'first_name': ''}
(hbnb) destroy User 06505348-0c86-4273-b1c2-68eefcbbab0c
(hbnb) show User 06505348-0c86-4273-b1c2-68eefcbbab0c
** no instance found **
```

The "all" command prints all string representation of all instances and the "update" command is used to update the User information. In the example below, the first name is updated to "Betty". Everything can be updated except the id, created and updated datetime.

```
(hbnb) update BaseModel 49faff9a-6318-451f-87b6-910505c55907 first_name "Betty"
(hbnb) show BaseModel 49faff9a-6318-451f-87b6-910505c55907
[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'first_name': 'Betty', 'id': '49faff9a-6318-451f-87b6-910505c55907', 'created_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903293), 'updated_at': datetime.datetime(2017, 10, 2, 3, 11, 3, 49401)}
```

## Bugs
No known bugs at this time. 

## Authors
* Abulele Ntulini - [Email](ntuliniabulele2@gmail.com)
* Chris Nwabueze - [Email] (gen.chriscruz@outlook.com)

## License
Public Domain. No copy write protection. 
