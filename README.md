# AirBnB Clone [The Console]

This project is the first step towards building a full web application: the AirBnB clone.

It is very important because it serves as the back-end base of other projects: HTML/CSS templating, database storage, API, front-end integration…

![AirBnB Logo](AirBnB_Logo.png) ![Holberton Logo](Holberton_Logo.png)

## Synopsis

### The Console

This software is a command interpreter similar to a Linux shell but limited to a specific use-case; management of objects in the AirBnB Clone:

- Creating new objects (e.g., a new User or a new Place)
- Retrieving an object from a file, a database, etc…
- Doing operations on objects (count, compute stats, etc…)
- Updating attributes of an object
- Destroying an object

It can work in two different modes:

- Interactive and Non-interactive.

In Interactive mode, the console will display a prompt (hbnb) indicating that the user can write and execute a command. After the command is run, the prompt will appear again and wait for a new command. This can go indefinitely as long as the user does not exit the program.

```shell
$ ./console.py
(hbnb) help

Documented commands (type help <topic>):
========================================
EOF  help  quit

(hbnb) 
(hbnb) 
(hbnb) quit
$
```

In Non-interactive mode, the shell will need to be run with a command input piped into its execution so that the command is run as soon as the Shell starts. In this mode, no prompt will appear, and no further input will be expected from the user.

```shell
$ echo "help" | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb) 
$
$ cat test_help
help
$
$ cat test_help | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb) 
$
```

## Format of Command Input

In order to give commands to the console, these will need to be piped through an echo in case of Non-interactive mode.

In Interactive Mode, the commands will need to be written with a keyboard when the prompt appears and will be recognized when an enter key is pressed (new line). As soon as this happens, the console will attempt to execute the command through several means or will show an error message if the command didn't run successfully. In this mode, the console can be exited using the CTRL + D combination, CTRL + C, or the command quit or EOF.

## Arguments

Most commands have several options or arguments that can be used when executing the program. In order for the Shell to recognize those parameters, the user must separate everything with spaces.

### Example:

```shell
user@ubuntu:~/AirBnB$ ./console.py
(hbnb) create BaseModel
49faff9a-6318-451f-87b6-910505c55907
user@ubuntu:~/AirBnB$ ./console.py

or

user@ubuntu:~/AirBnB$ ./console.py $ echo "create BaseModel" | ./console.py
(hbnb)
e37ebcd3-f8e1-4c1f-8095-7a019070b1fa
(hbnb)
user@ubuntu:~/AirBnB$ ./console.py
```

## Commands

The recognizable commands by the interpreter are the following:

| Command | Description |
| ------- | ----------- |
| quit or EOF | Exits the program |
| help | Provides a text describing how to use a command |
| create | Creates a new instance of a valid Class, saves it (to the JSON file) and prints the id. Valid classes are: BaseModel, User, State, City, Amenity, Place, Review |
| show | Prints the string representation of an instance based on the class name and id |
| destroy | Deletes an instance based on the class name and id (saves the change into a JSON file) |
| all | Prints all string representation of all instances based or not on the class name |
| update | Updates an instance based on the class name and id by adding or updating attribute (saves the changes into a JSON file) |
| count | Retrieve the number of instances of a class |

## Getting Started

These instructions will get you a copy of the project up and running on your local machine (Linux distro) for development and testing purposes.

### Installing

You will need to clone the repository of the project from Github. This will contain the simple shell program and all of its dependencies.

```shell
git clone https://github.com/jzamora5/AirBnB_clone.git
```

After cloning the repository you will have a

 folder called AirBnB_clone. In here there will be several files that allow the program to work.

- `console.py`: The main executable of the project, the command interpreter.

- `models/engine/file_storage.py`: Class that serializes instances to a JSON file and deserializes JSON file to instances.

- `models/__init__.py`: A unique FileStorage instance for the application.

- `models/base_model.py`: Class that defines all common attributes/methods for other classes.

- `models/user.py`: User class that inherits from BaseModel.

- `models/state.py`: State class that inherits from BaseModel.

- `models/city.py`: City class that inherits from BaseModel.

- `models/amenity.py`: Amenity class that inherits from BaseModel.

- `models/place.py`: Place class that inherits from BaseModel.

- `models/review.py`: Review class that inherits from BaseModel.

In the tests folders, several test files can be found which serve as unit-tests for the console.

### Testing

The program runs on Python3 which is an interpreted language, so it needs no compilation of any kind.

**Execution:**

To execute the console, the following code can be used:

**Interactive mode:**

```shell
test@ubuntu:~/simple_shell$ ./console
```

**Non-interactive mode:**

```shell
test@ubuntu:~/simple_shell$ echo "command" | ./console
```

### General Use Examples

**Interactive Mode:**

```shell
user@ubuntu:~/AirBnB$ ./console.py
(hbnb) create BaseModel
49faff9a-6318-451f-87b6-910505c55907
(hbnb) all BaseModel
["[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'created_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903293), 'id': '49faff9a-6318-451f-87b6-910505c55907', 'updated_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903300)}"]
(hbnb) show BaseModel 49faff9a-6318-451f-87b6-910505c55907
[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'created_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903293), 'id': '49faff9a-6318-451f-87b6-910505c55907', 'updated_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903300)}
(hbnb) update BaseModel 49faff9a-6318-451f-87b6-910505c55907 first_name "Betty"
(hbnb) show BaseModel 49faff9a-6318-451f-87b6-910505c55907
[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'first_name': 'Betty', 'id': '49faff9a-6318-451f-87b6-910505c55907', 'created_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903293), 'updated_at': datetime.datetime(2017, 10, 2, 3, 11, 3, 49401)}
(hbnb) create BaseModel
2dd6ef5c-467c-4f82-9521-a772ea7d84e9
(hbnb) all BaseModel
["[BaseModel] (2dd6ef5c-467c-4f82-9521-a772ea7d84e9) {'id': '2dd6ef5c-467c-4f82-9521-a772ea7d84e9', 'created_at': datetime.datetime(2017, 10, 2, 3, 11, 23, 639717), 'updated_at': datetime.datetime(2017, 10, 2, 3, 11, 23, 639724)}", "[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'first_name': 'Betty', 'id': '49faff9a-6318-451f-87b6-910505c55907', 'created_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903293), 'updated_at': datetime.datetime(2017, 10, 2, 3, 11, 3, 49401)}"]
(hbnb) destroy BaseModel 49faff9a-6318-451f-87b6-910505c55907
(hbnb) show BaseModel 49faff9a-6318-451f-87b6-910505c55907
** no instance found **
(hbnb)
```

**Non-Interactive Mode:**

```shell
user@ubuntu:~/AirBnB$ echo "create BaseModel" | ./console.py
(hbnb)
49faff9a-6318-451f-87b6-910505c55907
(hbnb)

user@ubuntu:~/AirBnB$ echo "all BaseModel" | ./console.py
(hbnb)
["[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'created_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903293), 'id': '49faff9a-6318-451f-87b6-910505c55907', 'updated_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903300)}"]
(hbnb)

user@ubuntu:~/AirBnB$ echo "show BaseModel 49faff9a-6318-451f-87b6-910505c55907" | ./console.py
(hbnb)
[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'created_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903293), 'id': '49faff9a-6318-451f-87b6-910505c55907', 'updated_at': datetime.datetime(2017, 10, 2, 3, 10, 25, 903300)}(hbnb)
```

### Built with

Ubuntu 14.04, Emacs, and Python3 language.

## Authors

- AJADI Surprise Matthew | Github: [DRSUCCESS](https://github.com/drsuccess)
Ziad Mohamed []

```

Please note that you should replace "AirBnB_Logo.png" and "Holberton_Logo.png" with the actual URLs or paths to your logo images, if you want to display them in your Markdown document.
