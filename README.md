# Web programming 2016a

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


## License
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This <span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" rel="dct:type">work</span> and all other materials under https://github.com/web-programming-2016s are licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
