#Smokeys-Encore Hello

On running the hello binary it asks the user to enter their name. On entering a dummy name we just get a simple greeting.
So let's let Ghidra analyze the file. 

Upon opening the hello file in Ghidra and having it analyze the binary we can see two functions that look interesting.
main and read_flag.
Well read_flag looks like it calls the flag variable from the environment and then prints it to the terminal
so let's take a look at main and try to see how we can get the program to call read_flag.

In the main function, we can see that read_flag is called when the local_c variable is not zero. 
We can also see that what we enter when prompted for a name is stored at a memory location right next to local_c
in a variable local_48.
While local_48 is only supposed to contain 60 characters there doesn't seem to be any checks in place to stop us from entering more 
