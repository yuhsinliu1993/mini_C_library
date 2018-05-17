# Mini C library

We are attempting to replace the standard C library with our hand-designed mini C library. 

Using `-nostdlib` to disable any standard library, but only the functions in `libminic.asm` file

The following commands show how to assemble, compile, link, and test the codes.

    # How to compile:
    $ yasm -f elf64 libminic.asm -o libminic.o
    $ ld -shared -o libminic.so libminic.o
    $ gcc -c -g -Wall -fno-stack-protector test1.c
    $ gcc -nostdlib -o test1 test1.o start.o libminic.o
    $ gcc -nostdlib -o test1s test1.o start.o libminic.so

TODO
----
- [ ] write: write data to a specific file descriptor
- [ ] setjmp: prepare for long jump by saving the current CPU state. In addition, preserve the signal mask of the current process.
- [ ] longjmp: perform the long jump by restoring a saved CPU state. In addition, restore the preserved signal mask.
- [ ] sigaction: setup the handler of a signal.
- [ ] sigprocmask: can be used to block/unblock signals, and get/set the current signal mask.
- [ ] alarm: setup a timer for the current process.
- [ ] pause: suspend the execution of the current process until a signal is delivered.
- [ ] sleep: suspend the execution of the current process for a given period.
- [ ] exit: terminate the current process.

