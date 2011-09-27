Subleq Quine
============

This is a [quine](http://en.wikipedia.org/wiki/Quine_(computing\)) written in
[`subleq`](http://en.wikipedia.org/wiki/One_instruction_set_computer#Subtract_and_branch_if_less_than_or_equal_to_zero)
("SUbtract and Branch if Less than or EQual to zero"), a universal instruction.
That means that `subleq`, alone, can accomplish anything a traditional computer
can. It is the [ultimate reduced instruction set computer (RISC)](http://en.wikipedia.org/wiki/One_instruction_set_computer).


The `subleq` instruction takes three arguments, *a*, *b*, and *c*. It
subtracts the contents at address *a* from the contents stored at address *b*,
stores the results at address *b* and then, if the result is not positive, 
jumps to address *c*. If the result is positive, execution proceeds to the next
instruction. Believe it or not, any other computational operation can be achieved
using some combination of `subleq` instructions (much like any logical gate can
be built from NAND gates)! For example addition can be accomplished like this:

    ADD a, b == subleq a, Z
                subleq Z, b
                subleq Z, Z

`Z` refers to a special location in memory that should always contain zero.
That's why the last operation is `subleq Z, Z`. It resets `Z` to zero.

Use
---

To use, you'll have to download the `subleq` assembler [here](http://mazonka.com/subleq/sqasm.cpp)
and the `subleq` emulator [here](http://mazonka.com/subleq/sqrun.cpp). 
Compile both `C++` files. To assemble and run the quine and save the output into
a file called `tmp` execute the following:

    ./sqasm < quine.sq | ./sqrun -stdin > tmp

Check that it actually is a quine:
    
    diff quine.sq tmp
