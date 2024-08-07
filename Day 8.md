---
day: 8
title: "File Operations"
description: "Covering File Operations, File Modes, Error Handling, and Standard Library Functions for File Handling"
---

# Day 8 - File Operations

## File Operations

### Opening a File
A file can be opened using the `fopen()` function, which returns a file pointer.
```c
FILE* fp = fopen("example.txt", "r");
```

### Reading from a File
Data can be read from a file using the fread function.
```c
char buffer[100];
fread(buffer, sizeof(char), 100, fp);
```

### Writing to a File
Data can be written to a file using the fwrite function.
```c
char* data = "Hello, World!";
fwrite(data, sizeof(char), strlen(data), fp);
```

### Closing a File
A file can be closed using the fclose() function.
```c
fclose(fp);
```

## File Modes

### Text Mode
In text mode, files are opened in a way that allows for reading and writing text data.
```c
FILE* fp = fopen("example.txt", "r");
```

### Binary Mode
In binary mode, files are opened in a way that allows for reading and writing binary data.
```c
FILE* fp = fopen("example.bin", "rb");
```

## Error Handling in File Operations

### Checking for Errors
Errors can be checked using the ferror function.
```c
if (ferror(fp)) {
    printf("Error occurred while reading file\n");
}
```

### Handling Errors
Errors can be handled using the perror function.
```c
if (fopen("example.txt", "r") == NULL) {
    perror("Error opening file");
}
```

## Standard Library Functions for File Handling

### fopen()
Opens a file and returns a file pointer.  
**Syntax:** fopen(path, mode);

The different modes available:
| Mode | Description |
| --- | --- |
| r | Only read. |
| w | Only write. If the file does not exist, it will be created. |
| a | Only append. If the file does not exist, it will be created. |
| r+ | Read and write. The file pointer is positioned at the beginning of the file. |
| w+ | Read and write. The file pointer is positioned at the beginning of the file. |
| a+ | Read and append. The file pointer is positioned at the end of the file. |
```c
FILE* fp = fopen("example.txt", "r");
```

### fclose()
Closes a file.
```c
fclose(fp);
```

### fread()
Reads data from a file.  
**Syntax**: fread(dest_var, size_of_char, no_of_characters, file_pointer);
```c
char buffer[100];
fread(buffer, sizeof(char), 100, fp);
```

### fwrite()
Writes data to a file.  
**Syntax**: fwrite(src_var, size_of_char, no_of_characters, file_pointer);
```c
char* data = "Hello, World!";
fwrite(data, sizeof(char), strlen(data), fp);
```

### fseek()
Moves the file pointer to a specified location.  
**Syntax**: fwrite(file_pointer, offset_amount, position_code);

For position_code, we have 3 macros:
| position_code | Description |
| --- | --- |
| SEEK_SET | Beginning of the file |
| SEEK_CUR | Current position in the file |
| SEEK_END | End of the file |
```c
fseek(fp, 0, SEEK_SET);     // Beginning of file
fseek(fp, 10, SEEK_SET);    // 10 positions after beginning
fseek(fp, 40, SEEK_CUR);    // 10 positions after current position (10+40=50)
fseek(fp, 0, SEEK_END);     // Ending of file
fseek(fp, -5, SEEK_END);    // 5 positions before ending of file
```

### ftell()
Returns the current position of the file pointer.
```c
long pos = ftell(fp);
```

### rewind()
Moves the file pointer to the beginning of the file.
```c
rewind(fp);
```

### Example
```c
#include <stdio.h>

int main() {
    FILE* fp = fopen("example.txt", "w");
    if (fp == NULL) {
        perror("Error opening file");
        return 1;
    }
    char* data = "Hello, World!";
    fwrite(data, sizeof(char), strlen(data), fp);
    fclose(fp);
    return 0;
}
```

## Activity Problems
1. [MCQ 1](https://gist.github.com/galaxygamerman/b9bb496865026f9cebdea9a56f3f992d/raw/54078b048e369fa7e2560158296458f553ebc31c/Day8_1.md)
2. [MCQ 2](https://gist.github.com/galaxygamerman/b9bb496865026f9cebdea9a56f3f992d/raw/54078b048e369fa7e2560158296458f553ebc31c/Day8_2.md)
3. [MCQ 3](https://gist.github.com/galaxygamerman/b9bb496865026f9cebdea9a56f3f992d/raw/54078b048e369fa7e2560158296458f553ebc31c/Day8_3.md)
4. Try to re-write some of your previously done programs to write their outputs into text files, instead of the terminal.