# kinograd
A Design and Integration of Software Systems project

## Introduction
kinograd is a web application for managing movies, projections and projection viewers in cinemas.

## Instruction Manual
1. Make sure you have NodeJS installed and an active MySQL service is available.
2. Check out the source code from git
```groovy
git clone https://github.com/hspasov/kinograd.git
```
3. Properly configure kinograd/config/database.js
4. Create database
```groovy
node kinograd/scripts/createDatabase.js
```
5. Open kinograd main dir
```groovy
cd kinograd
```
6. Install dependencies
```groovy
npm install
```
7. Start application
```groovy
npm start
```
## Technologies used
ExpressJS, pugJS, Bootstrap and MySQL.

## Database tables
### Users
| Column      | Data type    | Constraints           |
|:-----------:|:------------:|:---------------------:|
| Username    | VARCHAR(15)  | NOT NULL, PRIMARY KEY |
| Password    | VARCHAR(60)  | NOT NULL              |
| FirstName   | VARCHAR(30)  | NOT NULL              |
| LastName    | VARCHAR(30)  | NOT NULL              |
| DateOfBirth | DATE         | NOT NULL              |
| ProfilePic  | VARCHAR(255) | NOT NULL              |
| Role        | VARCHAR(20)  | NOT NULL              |

### Movies
| Column              | Data type     | Constraints           |
|:-------------------:|:-------------:|:---------------------:|
| Id (AUTO_INCREMENT) | INTEGER       | NOT NULL, PRIMARY KEY |
| Title               | VARCHAR(100)  | NOT NULL              |
| AgeRestriction      | INTEGER       | NOT NULL              |
| Premiere            | DATE          | NOT NULL              |
| Length              | INTEGER       | NOT NULL              |
| Description         | VARCHAR(1000) | NOT NULL              |
| Image               | VARCHAR(255)  | NOT NULL              |

### Halls
| Column              | Data type    | Constraints           |
|:-------------------:|:------------:|:---------------------:|
| Id                  | INTEGER      | NOT NULL, PRIMARY KEY |
| Seats               | INTEGER      | NOT NULL              |

### Projections
| Column              | Data type    | Constraints                                 |
|:-------------------:|:------------:|:-------------------------------------------:|
| Id (AUTO_INCREMENT) | INTEGER      | NOT NULL, PRIMARY KEY                       |
| MovieId             | INTEGER      | NOT NULL, FOREIGN KEY REFERENCES Movies(Id) |
| HallId              | INTEGER      | NOT NULL, FOREIGN KEY REFERENCES Halls(Id)  |
| StartTime           | DATETIME     | NOT NULL                                    |

### ProjectionViewers
| Column              | Data type    | Constraints                                      |
|:-------------------:|:------------:|:------------------------------------------------:|
| Id (AUTO_INCREMENT) | INTEGER      | NOT NULL, PRIMARY KEY                            |
| ProjectionId        | INTEGER      | NOT NULL, FOREIGN KEY REFERENCES Projections(Id) |
| Username            | VARCHAR(15)  | NOT NULL, FOREIGN KEY REFERENCES Users(Username) |

## Contributors
Georgi Grazhdanski\
Hristo Spasov\
Simeon Tsvetkov\
Tanya Zheleva
