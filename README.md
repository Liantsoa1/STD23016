# LEVEL 00:
To reach the solution, here were the steps:
- I went to /home/level using the command `cd`.
- I used `cd` to go to the directory called "00_welcome."
- Inside that directory, there was a file named "README.md," and I read it using `cat`.
- It said that the solution to level 0 is: "bitwarrior" without the quotes.

# LEVEL 01:
In the /home/level directory, I went to "01_choice_tree."
- Inside it, there were three directories: "blue," "green," "red," and a file called README.md (that contained nothing important).
- Within the "blue" directory, there was another one called "hats."
- Inside "hats," there were also three directories: "black," "grey," "white."
- The solution was inside the "patience" directory that was inside "solution" that was also inside the "grey" directory.
- The patience directory contained the "SOLUTION.txt," which said: The solution to level 1 is "patience" without the quotes.

# LEVEL 02:
In the /home/level directory, I went inside the "02" directory.
- I used "ls -a" to show a hidden directory called ".porb."
- Inside ".porb," I also used "ls -a" to show a file called ".solution."
- By using "cat," I saw the content of the file, and it said: The solution is HiddenIsConfig.

# LEVEL 03:
In the /home/level directory, I went inside the "03" directory.
- Using "ls -a," I saw the hidden file called ".bash_history."
- The content of the hidden file was: The solution to SSH3 is: `RepeatingHistory`.

# LEVEL 04:
For this level, I didn't go to /home/level
- I needed to go to ~/level/04_kwisatz$
- Inside that directory, there is 2 file : README.txt and README2.md
- There is nothing important inside the README.txt
- The solution is inside README2.md
- it says => Your flag is: "AndOfCourseIDoKnowChown" without the quotes.

# LEVEL 05:
In the /home/level directory, I went inside the "05_privacy" directory.
- Inside that directory, there was a file called "README.md."
- By using "cat," I read that file, and it said: The 5th solution is "OKPRIVATE" without the quotes.

# LEVEL 10:
In the /home/level directory, I went inside the "10_choose_your_path" directory.
- There were files inside that directory: "charp," "charp.c," "compile.sh," and "solution.txt."
- There was no reading permission for the "solution.txt" file, but the "charp.c" file had execution permission.
- I read the source code of "charp" by using the command "nano charp.c."
- After examining the source code, it used the `popen` function to open a pipe to the command "/usr/bin/wc -l %s," where %s was replaced with the filename.
- The `popen()` function was used to execute a command.
- I used a method similar to injection to obtain the flag. I used the command here => ./charp "so & cat solution.txt > ~/answer.txt"
- After using that command, I could read the "answer.txt" file that was now in my home directory.
- The file said: The flag or solution for this challenge is: `EpidermalGlance`.

# LEVEL 12 :
This level is called pytong, they gave us a source code
- it is a type of code that executes a program based on the file name received through argv[1]
- the file name must not contain several strings such as proc, uptime, tmp, random
- after reading the file for the first time, it reads it again a little later, and if the contents of the two files are different, the information in Solution.txt is printed.
- I can solve it by creating a file in tmp and creating a symbolic link with ln.
- I turned on two consoles and created a generator that randomly generates files on one side, and simply ran Python on the other side to find the answer(./pytong ./checkopening./checkclosed)
- the result is : You are a winner Yep! your Solution is `KnowYourFilesChiller`.

# LEVEL 14:
The title of this level is LIVE LFI, it stands as Local File Inclusion.
So, I can manipulate input parameters in a way that tricks the application into including files that I should not have access to.
- first, I clicked on the link they gave, it lead to : https://lfi.warchall.net/
- I need to build this to try finding the solution : https://lfi.warchall.net/index.php?lang=solution.php
- the source code of that page says that : the flag is near!
- I tried to read the source code of the file by using : ?file=php://filter/read=convert.base64-encode/resource=index.php
- Then, we need to construct http://lfi.warchall.net/?lang=php://filter/read=convert.base64-encode/resource=solution.php
- that website gives us a Base64-encoded text : ICMgICBZT1VSX1RST1BIWSAKcmV0dXJuICdTdGVwcGluU3RvbmVzNDJQaWUnOyAjIDwtwrQgPz4K
- After Base64 decryption, we can get :
YOUR_TROPHY! return 'SteppinStones42Pie'; # <!� �>�
- the solution is `SteppinStones42Pie`

# LEVEL 15 :
The next level is LIVE RFI, it stands as Remote File Inclusion
So, I can include files from the link they gave me : https://rfi.warchall.net/
- same as the LFI challenge, we need to construct
- I constructed this : http://rfi.warchall.net/index.php?lang=php://filter/read=convert.base64-encode/resource=solution.php.
- that website gives us a Base64-encoded text : A8P3BocCByZXR1cm4gJ0xvd19INE5HSU5HX0ZydWl0JzsgPz4K
- After Base64 decryption, we can get :
<?php return 'Low_H4NGING_Fruit'; ?>
- the solution is `Low_H4NGING_Fruit`

