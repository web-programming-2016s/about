# Web programming 2016s

* **Course overview:** [IFI6076](http://www.cs.tlu.ee/instituut/oppe_tegevus/kp/kp_k_2016/)
* **Teacher:** Romil Rõbtšenkov, [romilr@tlu.ee](mailto:romilr@tlu.ee)
* **Test server:** greeny.cs.tlu.ee
* **Lesson examples:** ~romil/wp16s
* **Style guide:** [Coding Style Guide](http://www.php-fig.org/psr/psr-2/)
* **GIT tutorial:** [Become a git guru.](https://www.atlassian.com/git/tutorials/)
* **Resources:** [Veebirakenduste loomine PHP ja MySQLi abil](http://minitorn.tlu.ee/~jaagup/kool/java/loeng/veebipr/veebipr1.pdf), [PHP with MySQL Essential Training] (http://www.lynda.com/MySQL-tutorials/PHP-MySQL-Essential-Training/119003-2.html)

## Homeworks and projects

All homeworks can be found in course outline.

### Connecting to greeny server

* Windows | [VIDEO](https://youtu.be/kg5NAsRQAJ8)

    * [Guide to create tunnel (in estonian, but with screenshots)](http://minitorn.tlu.ee/~jaagup/kool/java/kursused/09/veebipr/naited/greenytunnel/greenytunnel.pdf)

* Mac OS | [VIDEO](https://youtu.be/RJc-Gvpn9M4)
```
1. open Terminal app

2. write:
ssh university_username@lin2.tlu.ee -L 5555:greeny.cs.tlu.ee:80
3. then write TLU password

    Now you can access greeny from browser localhost:5555

3. open new tab in Terminal (cmd+t) and write:
ssh university_username@lin2.tlu.ee -L 2222:greeny.cs.tlu.ee:22
4. then write TLU password

5. now open FTP client (CyberDuck, FileZilla, Coda) for example and connect to greeny via SFTP
    host: localhost or some require 127.0.0.1 (127.0.0.1 = localhost)
    port: 2222
    username: your_greeny_username
    password: your_greeny_username

6. choose one Terminal tab and connect to greeny via ssh, write:
ssh greeny_username@greeny.cs.tlu.ee
7. then enter your Greeny username password
    ls             – to view files and folders in current path
    cd folder_name - to enter folder
    cd ..          – to exit folder to previous path

```

### GitHub workflow

1. *Fork*'i taks/project repository (can be found [github.com/web-programming-2016s](https://github.com/web-programming-2016s)).
1. *Clone* the repository to your computer/server. Append your username to let *git* know, who you are.
  ```
  git clone https://USERNAME@github.com/USERNAME/REPOSITORY.git
  ```
1. Add and update files to complete given task, *Commit* every important change using two statements.
  ```
  git add .
  ```
  ```
  git commit -m "Added this functionality to the app"
  ```
1. Check if all of the code is *Commit*'ed.
  ```
  git status
  ```
1. *Push/sync* it to GitHub.
  ```
  git push origin master
  ```
1. [Open *pull request*](https://help.github.com/articles/creating-a-pull-request) in the task repository. Deadline is the next lesson if not stated otherwise.
1. Changes and addtitions can be *push*'ed to repository until the deadline.

I will give feedback by adding comments under *pull request*'s where you can added your comments/thoughts/feedback/questions. You can create *pull request* right away when you start working and then add questions there. Mention my username in the comments `@romilrobtsenkov` for faster reply, sometimes.

### Requirements

They are valid also in real life!

* Good programming style
    * Keep function name "short"
    * Optimize code for reading
    * Object oriented approach should be used with projects
    * Borrowed code needs to be cited
* Bonus:
    * Creativity (NB! Requirements should be still fullfilled)

## Course outline

### 1 lesson

1. Introduction
    * About course
    * Introduction
        * Name
        * Your interests and hobbies
        * How you ended up in this subject
1. Prep
    * Install GitHub [Mac](https://mac.github.com) or for windows [Windows](https://windows.github.com) (if you are using personal computer)
    * Create user to [GitHub](https://github.com/)
1. Testing GitHub workflow
1. Few lines of code (Hello world)

### 2 lesson

1. Connecting to greeny and using GitHub for version control
1. intro to PHP
    * variables
    * logical operators, if statement
    * for loop
    * using date and [php.net](http://php.net) documentation

### 3 lesson

1. Ceating [HTML form](http://www.w3schools.com/html/html_forms.asp)
1. Validating fields
```PHP
   isset($_GET["name"]){
      //varialbe name exists (?name="Romil") in the URL http://www.romil.ee/hello.php?name="Romil"
   }else{
      //there is no variable name in the URL http://www.romil.ee/hello.php
   }    
   
   
   empty($_GET["name"]){
      //varialbe name in the URL is empty or empty string http://www.romil.ee/hello.php?name= OR http://www.romil.ee/hello.php?name=""
   }else{
      //there is value Romil in the variable  URL http://www.romil.ee/hello.php?name="Romil"
   }    
```
1. Added [1. homework](https://github.com/web-programming-2016s/1.homework)

### 4 lesson

1. Creating a [database](http://www.w3schools.com/sql/sql_create_db.asp), [table](http://www.w3schools.com/sql/sql_create_table.asp) and [inserting rows](http://www.w3schools.com/sql/sql_insert.asp). Used commands: 
```SQL
mysqli -uUsername -pPassword

CREATE DATABASE databaseusername_greenyusername;

CREATE TABLE IF NOT EXISTS `messages_sample` (
  `id` int(11) NOT NULL,
  `recipient` varchar(255) NOT NULL,
  `message` varchar(255) NOT NULL,
  `created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `deleted` timestamp NULL DEFAULT NULL
); 

INSERT INTO `messages_sample`(`recipient`, `message`) VALUES ("romil@romil.romil", "test")
```
2. Using greeny.cs.tlu.ee/phpMyadmin -> you can access it from home localhost:5555/phpMyAdmin

### 5 lesson
1 Separate configuration file outside of project folder
```PHP
//config.php
<?php
	
	$db_username = "username";
	$db_password = "password";

?>
```
2 Insert into database
```PHP
require_once("../config.php");
$mysql = new mysqli("localhost", $db_username, $db_password, "webpr2016_romil");
$stmt = $mysql->prepare("INSERT INTO messages_sample (recipient, message) VALUES (?,?)");
echo $mysql->error;

// we are replacing question marks with values
// s - string, date or smth that is based on characters and numbers
// i - integer, number
// d - decimal, float

//for each question mark its type with one letter
$stmt->bind_param("ss", $_GET["to"], $_GET["message"]);

if($stmt->execute()){
	echo "saved sucessfully";
}else{
	echo $stmt->error;
}
```
3. Getting data from database 
```PHP
require_once("../config.php");
$mysql = new mysqli("localhost", $db_username, $db_password, "webpr2016_romil");
$stmt = $mysql->prepare("SELECT id, recipient, message, created FROM messages_sample ORDER BY created DESC LIMIT 10");
echo $mysql->error;
$stmt->bind_result($id, $recipient, $message, $created);
$stmt->execute();
while($stmt->fetch()){
	//DO SOMETHING FOR EACH ROW
	echo $id." ".$message."<br>";
}
```
### 6 lesson
1 Added [Bootstrap](http://getbootstrap.com) 
2 Archiving in database
```PHP
if(isset($_GET["delete"])){
		
		echo "Deleting row with id:".$_GET["delete"];
		
		// NOW() = current date-time
		$stmt = $mysql->prepare("UPDATE messages_sample SET deleted=NOW() WHERE id = ?");
		
		echo $mysql->error;
		
		//replace the ?
		$stmt->bind_param("i", $_GET["delete"]);
		
		if($stmt->execute()){
			echo "deleted successfully";
		}else{
			echo $stmt->error;
		}
		
		//closes the statement, so others can use connection
		$stmt->close();
}

```
### 7 lesson
1 Updating data
```PHP
if(isset($_GET["to"]) && isset($_GET["message"])){
   $stmt = $mysql->prepare("UPDATE messages_sample SET recipient=?, message=? WHERE id=?");
   			
   echo $mysql->error;
   
   $stmt->bind_param("ssi", $_GET["to"], $_GET["message"], $_GET["edit"]);
   
   if($stmt->execute()){
   	
   	echo "saved successfully"; 
   	
   }else{
   	echo $stmt->error;
   }
}
```

### 8 lesson
1 To forward user, use
```PHP
header("Location: login.php");
```
2 Using session
```PHP
//start session, make use of session variables possible
session_start();

//assign value
$_SESSION["name"] = "Romil";

//destroy session on logout, makes session variables undefined
session_destroy();
```
3 Hashing password 
```PHP
$pass = "romilromil";

$pass = hash("sha512", $pass);

// now $pass equals:
// 922de38b118464a94bfceeb00de53f88f9161597fdd2028d4ee4441920cef83a1c7cc29b9818b2858b59f3a3f66f042c66d8a49dacc29d24d130eb736e1884bc
```

### 9 lesson
1 creating connected tables
```SQL
CREATE TABLE IF NOT EXISTS `users` (
  `id` int(11) NOT NULL,
  `name` varchar(255) NOT NULL,
  `username` varchar(255) NOT NULL,
  `password` varchar(128) NOT NULL
);
ALTER TABLE `users`
  ADD PRIMARY KEY (`id`),
  ADD UNIQUE KEY `username` (`username`);


CREATE TABLE IF NOT EXISTS `interests` (
  `id` int(11) NOT NULL,
  `name` varchar(255) NOT NULL
);
ALTER TABLE `interests`
  ADD PRIMARY KEY (`id`),
  ADD UNIQUE KEY `name` (`name`);


CREATE TABLE IF NOT EXISTS `users_interests` (
  `id` int(11) NOT NULL,
  `user_id` int(11) NOT NULL,
  `interests_id` int(11) NOT NULL
);
ALTER TABLE `users_interests`
  ADD PRIMARY KEY (`id`),
  ADD KEY `user_id` (`user_id`),
  ADD KEY `interests_id` (`interests_id`);

/* Connecting tables */

ALTER TABLE `users_interests`
  ADD CONSTRAINT `users_interests_ibfk_1` FOREIGN KEY (`user_id`) REFERENCES `users` (`id`),
  ADD CONSTRAINT `users_interests_ibfk_2` FOREIGN KEY (`interests_id`) REFERENCES `interests` (`id`);

```
2 Quering from multiple tables
```SQL
SELECT interests.name FROM users_interests
INNER JOIN interests ON
users_interests.interests_id = interests.id
WHERE users_interests.user_id = ?
```
### 10 lesson
```
git fetch

git pull

git config user.name "Romil Robtsenkov"

git config user.email "romilrobtsenkov@users.noreply.github.com"
```

## License
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This <span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" rel="dct:type">work</span> and all other materials under https://github.com/web-programming-2016s are licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
