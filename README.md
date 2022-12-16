0x19. C - Stacks, Queues - LIFO, FIFO

Data structures

Please use the following data structures for this project. Don’t forget to include them in your header file.



/**

 * struct stack_s - doubly linked list representation of a stack (or queue)

 * @n: integer

 * @prev: points to the previous element of the stack (or queue)

 * @next: points to the next element of the stack (or queue)

 *

 * Description: doubly linked list node structure

 * for stack, queues, LIFO, FIFO

 */

typedef struct stack_s

{

        int n;

        struct stack_s *prev;

        struct stack_s *next;

} stack_t;

/**

 * struct instruction_s - opcode and its function

 * @opcode: the opcode

 * @f: function to handle the opcode

 *

 * Description: opcode and its function

 * for stack, queues, LIFO, FIFO

 */

typedef struct instruction_s

{

        char *opcode;

        void (*f)(stack_t **stack, unsigned int line_number);

} instruction_t;

Compilation & Output

Your code will be compiled this way:

$ gcc -Wall -Werror -Wextra -pedantic -std=c89 *.c -o monty

Any output must be printed on stdout

Any error message must be printed on stderr

Here is a link to a GitHub repository that could help you making sure your errors are printed on stderr

Tests

We strongly encourage you to work all together on a set of tests



The Monty language

Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project is to create an interpreter for Monty ByteCodes files.



Monty byte code files



Files containing Monty byte codes usually have the .m extension. Most of the industry uses this standard but it is not required by the specification of the language. There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument:



julien@ubuntu:~/monty$ cat -e bytecodes/000.m

push 0$

push 1$

push 2$

  push 3$

                   pall    $

push 4$

    push 5    $

      push    6        $

pall$

julien@ubuntu:~/monty$

Monty byte code files can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:



julien@ubuntu:~/monty$ cat -e bytecodes/001.m

push 0 Push 0 onto the stack$

push 1 Push 1 onto the stack$

$

push 2$

  push 3$

                   pall    $

$

$

                           $

push 4$

$

    push 5    $

      push    6        $

$

pall This is the end of our program. Monty is awesome!$

julien@ubuntu:~/monty$
