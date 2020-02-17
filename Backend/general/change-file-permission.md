## How to change file permissions in terminal

Date: 2019-09-03

chmod <3-digit-number> \<directory>

ex) chmod 777 /data/db

-  what do the numbers mean?
  - read is equivalent to 4
  - write is equivalent to 2
  - execute is equivalent to 1
  - 0 – no permission
    1 – execute (1)
    2 – write (2)
    3 – write and execute (2 + 1)
    4 – read (4)
    5 – read and execute (4 + 1)
    6 – read and write (4 + 2)
    7 – read, write, and execute (4 + 2 + 1)

- Digits
  - first digit is assigned to the Owner
  - second digit is assigned to the Group
  - third digit is assigned to the Others

[What does chmod 777 mean?](https://www.maketecheasier.com/file-permissions-what-does-chmod-777-means/)