#0x19. C - Stacks, Queues LIFO, FIFO
Requirements
Usage: monty file
Any output must be printed on stdout
Any error message must be printed on stderr
There is not more than one instruction per line
There can be any number of spaces before or after the opcode and its argument
The monty program runs the bytecodes line by line and stop if either:
it executed properly every line of the file
it finds an error in the file
an error occured
If the user does not give any file or more than one argument to your program, we print the error message USAGE: monty file, followed by a new line, and exit with the status EXIT_FAILURE
if the file contains an invalid instruction, we print the error message L<line_number>: unknown instruction <opcode>, followed by a new line, and exit with the status EXIT_FAILURE
Line numbers always start at 1
If we can’t malloc anymore, we print the error message Error: malloc failed, followed by a new line, and exit with status EXIT_FAILURE
We suppose to use Those structures : /**
struct stack_s - doubly linked list representation of a stack (or queue)
@n: integer
@prev: points to the previous element of the stack (or queue)
@next: points to the next element of the stack (or queue)
Description: doubly linked list node structure
for stack, queues, LIFO, FIFO */ typedef struct stack_s { int n; struct stack_s *prev; struct stack_s *next; } stack_t;
/**

struct instruction_s - opcode and its function
@opcode: the opcode
@f: function to handle the opcode
Description: opcode and its function
for stack, queues, LIFO, FIFO */ typedef struct instruction_s { char *opcode; void (*f)(stack_t **stack, unsigned int line_number); } instruction_t;
Opcodes:
push - Push an elements to the stack.
pall - Prints all the values on the stack, starting from the top of the stack.
pint - Prints the value at the top of the stack, followed by a new line.
pop - Removes the top element of the stack.
swap - Swaps the top two elements of the stack.
add - Adds the top two elements of the stack.
sub - Subtracts the top element of the stack from the second top element of the stack.
div - Divides the second top element of the stack by the top element of the stack.
mul - Multiplies the second top element of the stack with the top element of the stack.
mod - Computes the rest of the division of the second top element of the stack by the top element of the stack.
pchar - Prints the char at the top of the stack, followed by a new line.
pstr - Prints the string starting at the top of the stack, followed by a new line.
rotl - Rotates the stack to the top.
rotr - Rotates the stack to the bottom.
stack - Sets the format of the data to a stack (LIFO). This is the default behavior of the program.
queue - Sets the format of the data to a queue (FIFO).
