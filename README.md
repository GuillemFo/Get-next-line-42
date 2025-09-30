# Get Next Line - Reading a line from a file descriptor

## 🎯 Project Overview

**Get Next Line** is a fundamental C programming project that teaches you how to read content from a file descriptor line by line. This project introduces the important concept of **static variables** while solving a common real-world programming problem.

> **Summary:** This project is about programming a function that returns a line read from a file descriptor.

## 💡 Project Concept

The goal is to create a function that can read from any file descriptor (files, standard input, etc.) and return one complete line at a time with each function call. This is much more efficient than reading entire files into memory.

## 🛠️ Function Specification

### Basic Function Details
| Component | Specification |
|-----------|---------------|
| **Function Name** | `get_next_line` |
| **Prototype** | `char *get_next_line(int fd)` |
| **Parameters** | `fd`: File descriptor to read from |
| **Return Value** | Read line (including `\n`) or `NULL` on EOF/error |
| **External Functions** | `read`, `malloc`, `free` |

### Key Requirements
- **Read files line by line** through repeated function calls
- **Return lines with `\n` character** (except at end of file)
- **Work with any file descriptor** (files, stdin, etc.)
- **Handle variable buffer sizes** using `-D BUFFER_SIZE=n`
- **Use static variables** to maintain state between calls

## 🔧 Implementation Rules


### Technical Constraints
- ✅ **Must use static variables** to preserve reading state
- ✅ **Handle any BUFFER_SIZE** (1, 9999, 10000000, etc.)
- ✅ **Read minimal data** each call (stop at newline)
- ❌ **No libft allowed**
- ❌ **No lseek() function**
- ❌ **No global variables**
- ❌ **No reading entire file at once**

### Compilation Requirements  
# Compile with custom buffer size
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c

# Must also compile without BUFFER_SIZE flag
cc -Wall -Wextra -Werror get_next_line.c get_next_line_utils.c

## 🎯 Learning Objectives

- **Static Variables**: Understand and implement persistent data between function calls
- **File Descriptor Management**: Work with different input sources
- **Memory Management**: Proper allocation and freeing of line buffers
- **Buffer Handling**: Efficient reading with variable buffer sizes
- **Edge Case Handling**: EOF, empty files, very long lines, etc.

## 🏆 Bonus Part
*Only if mandatory part is PERFECT*

### Bonus Requirements
- **Single static variable** implementation
- **Multiple file descriptor** support
  - Read from different FDs interchangeably
  - Maintain separate reading states for each FD
  - Example: Read from FD 3, then 4, then 5, then back to 3

## ⚠️ Important Notes

### Expected Behavior
- **Include `\n`** in returned lines (except at EOF)
- **Return `NULL`** when nothing left to read or on error
- **Handle binary files** (undefined behavior, but can implement logic)
- **Undefined behavior** if file modified during reading

### Testing Considerations
- **Test with various BUFFER_SIZE values** (1, small, large, very large)
- **Test different line lengths** (short, long, very long)
- **Test different file types** (regular files, stdin, empty files)
- **Test multiple file descriptors** (for bonus)

## 📝 Implementation Tips

1. **Use a static buffer** to store leftover data between calls
2. **Read in chunks** defined by BUFFER_SIZE
3. **Stop reading** when you find a newline character
4. **Handle EOF** when read returns 0
5. **Manage memory properly** - free allocated lines
6. **Return complete lines** including the `\n` character

## 🔍 Common Challenges

- **Memory management** with variable buffer sizes
- **Handling very long lines** that exceed BUFFER_SIZE
- **Maintaining state** between function calls
- **Efficiently finding newlines** in buffered data
- **Proper error handling** for file operations

---

*Master file I/O operations and static variables while building a versatile line-reading function that can handle any input source efficiently!*
