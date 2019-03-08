# Reference-Monitor
This is a computer security class project to implement a defensive security system using Python and Repy V2 API.
In this assignment you will create a security layer which keeps a backup copy of a file in case it is written incorrectly. This is a common technique for things like firmware images where a system may not be able to recover if the file is written incorrectly. For this assignment, a valid file must start with the character 'S' and end with the character 'E'. If any other characters (including lowercase 's', 'e', etc.) are the first or last characters, then the file is considered invalid.

Applications use ABopenfile() to create or open a file. Files are created by setting create=True when calling ABopenfile(), the reference monitor will create a new file 'SE' in filename.a and an empty file called filename.b. When close() is called on the file, if a file is not valid, it is discarded. If both files are valid, the older one is discarded.

Write test applications to ensure your reference monitor behaves properly in different cases and to test attacks against your monitor.

The Reference Monitor Must:
Not modify or disable any functionality of any RepyV2 API calls, such as:
Creating new files
Opening an existing file
Reading valid file using readat()
Writing to file using writeat(). This includes invalid writes, because 'S' and 'E' may later be written to the begining and end of the file respectively.
Check if the file starts with 'S' and ends with 'E', only when close() is called.
Not produce any errors
Normal operations should not be blocked or produce any output
Invalid operations should not produce any output to the user
The Reference Monitor Should:
Store two copies of the same file (filename.a and filename.b)
One is a valid backup, and the other is written to
When an app calls ABopenfile(), the method opens the A/B files, which you should name filename.a and filename.b.
When the app calls readat(), all reads must be performed on the valid file
When the app calls writeat(), all writes must be performed on the invalid file.
Three design paradigms are at work in this assignment: accuracy, efficiency, and security.

Accuracy: The security layer should only stop certain actions from being blocked. All other actions should be allowed. For example, if an app tries to read data from a valid file, this must succeed as per normal and must not be blocked. All situations that are not described above must match that of the underlying API.

Efficiency: The security layer should use a minimum number of resources, so performance is not compromised. For example, keeping a complete copy of every file on disk in memory would be forbidden.

Security: The attacker should not be able to circumvent the security layer. Hence, if the attacker can cause an invalid file to be read or can write to a valid file, then the security is compromised, for example.
