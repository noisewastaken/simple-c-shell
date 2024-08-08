# A Simple Shell in C

This project is a basic implementation of a shell in C, created to enhance my understanding of the C programming language. It follows a straightforward structure to handle command-line input, parse it, and execute the corresponding commands.

### Main Loop: `lsh_loop`

The `lsh_loop` function is the core of the shell, performing three key steps:

1. **Read**: Reads the command from standard input (stdin).
2. **Parse**: Splits the command string into a program and its arguments.
3. **Execute**: Runs the parsed command.

Here's the implementation:

```c
void lsh_loop(void) 
{
    char *line;
    char **args;
    int status;

    do {
        printf("> ");              // Print prompt
        line = lsh_read_line();     // Read the command
        args = lsh_split_line(line); // Parse the command
        status = lsh_execute(args);  // Execute the command

        free(line);  // Free the memory allocated for the line
        free(args);  // Free the memory allocated for the arguments
    } while(status);  // Continue until the status indicates to stop
}
```

- **Read**: The shell prints a prompt (`>`), waits for the user to input a command, and then reads the line of input.
- **Parse**: The input line is split into an array of arguments, where the first element is the program to be executed, and the subsequent elements are the arguments.
- **Execute**: The parsed command is then executed, and the shell waits for the next command.

### Project Motivation

This project was inspired by [Stephen Brennan's guide on writing a shell in C](https://brennan.io/2015/01/16/write-a-shell-in-c/). The primary goal was to deepen my understanding of C through a practical, hands-on approach.
