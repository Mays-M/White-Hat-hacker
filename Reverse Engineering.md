# Reverse Engineering: Lab05- 32-bit ELF-binary

## Main function of the program

""The code begins with the standard preamble. This sets up the stack frame and
allocates memory for local variables. The string "serial key: " is printed to
prompt the user for input. Input is read using scanf with “%s” as an argument. It
is stored in a buffer as a string. This is passed to the check_serial function for
validation.The result is checked.""

• _time: This function to retrieving the current time.
• _stand: to initialize the serial key number.
• _memset: to initial a block of memory [var_17] set to zero.
• _printf: to print the string “Insert serial key” to the console, prompting
the user input.
• ___isoc99_scanf: it is readying user input and check if it is string.
• Check_serial: to check the user input validation.
• word ptr: it means the following operand is a 16-bit value located in memory
at a particular address. Reverse assembly is often used in debugging and
reverse engineering to understand the low-level details of a program or
binary executable.

### Check serial function

""The begin of this function start with set of codes to check the length of a string as
user input, it is obtained from the function argument =19 characters, and if True
jump to location in the memory call loc_804920A for further instructions.
After checking the condition, the function starts to set the serial instructions and
from the construction of the flow of the code we found:

• The key has 4 sets and in total are 16 and as we know that the key should be
19 so still 3 characters are still missing.

• Notice the code it is increasing by one and every 4 steps will pass one, so
from the code below we can see the first 4 codes it is loading 8-bits(byte)
from the memory and add 1 to the value in the register ecx and on the step 5
it is pass the 5th character so we know the forth character is missing and this
is continue for the other 3 sets so, we can set it to – or / or any other special
character except white space as we tested on the console, Now we know we
have key set like xxx-xxxx-xxx-xxx which in total it is 19
movsx ecx, byte ptr [ecx]
movsx ecx, byte ptr [ecx+1]
movsx ecx, byte ptr [ecx+2]
movsx ecx, byte ptr [ecx+3]
movsx ecx, byte ptr [ecx+5]

• The second step was to find that there are only two hexa numbers used as un
argument with ‘and’ which are 400h and 800h
400h=0000 0100 0000 0000
800h=0000 1000 000 0000
From this point I started to digging to know what the actual job of the function is
__ctype_b_loc and I found that this function:
• The __ctype_b_loc() function shall return a pointer into an array of characters
in the current locale that contains characteristics for each character in the
current character set.

Now to apply this on the two hexa number we had in our program, we found
it is return number on 800h and alphabets on 400h.
In this point we still missing the arrange of the set of the key and from our
code, I followed the use of 400h and 800h found it is return a set like this:


NAAN-NNAA-AANN-NNNA
*’N ‘presents 800h which is a Number and ‘A ‘presents 400h which is a letter.

## The Result
The serial key is 4 sets divided by -, it is alpha and numbers with no white space. The
character set base on the flow of the code as show in the figure above and tested on
5 different keys fellow the same instruction to generate a key base on the code instruction.

**visit:** https://braincoke.fr/blog/2018/05/what-is-ctype-b-loc/
