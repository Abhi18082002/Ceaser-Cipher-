# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a simple Caesar Cipher implementation in Python that provides interactive encryption and decryption functionality. The project consists of a single main script with ASCII art branding.

## Architecture

- **main.py**: Core application with Caesar cipher algorithm, interactive CLI, and main program loop
- **art**: ASCII art logo file (plain text, imported as a Python module despite the import error)

### Key Components

- **Caesar cipher function**: Handles both encoding and decoding with shift amount parameter
- **Interactive loop**: Continuous user interface for multiple encryption/decryption operations
- **Character handling**: Preserves non-alphabetic characters during transformation

## Common Commands

### Running the Application
```bash
python3 main.py
```

### Testing the Cipher Logic
```bash
# Test encoding
echo "hello" | python3 -c "
from main import caesar
caesar('hello', 5, 'encode')
"

# Test decoding  
echo "mjqqt" | python3 -c "
from main import caesar
caesar('mjqqt', 5, 'decode')
"
```

### Debugging
```bash
# Check syntax
python3 -m py_compile main.py

# Run with verbose output
python3 -v main.py
```

## Development Notes

### Current Issues
- The `import art` statement will fail since `art` is not a proper Python module (missing .py extension)
- The print statement inside the caesar function loop prints output multiple times
- The art logo is duplicated (defined in both art file and main.py)

### Code Structure
- Single function `caesar()` handles both encryption and decryption logic
- Uses modulo arithmetic for alphabet wrapping
- Preserves case by converting all input to lowercase
- Maintains non-alphabetic characters (spaces, punctuation) unchanged

### Testing Approach
Since this is an interactive script without formal tests, manual testing involves:
1. Testing various shift values (positive/negative/large numbers)
2. Testing edge cases (empty strings, non-alphabetic characters)
3. Verifying encode/decode reversibility
4. Testing the continuous operation loop

## File Dependencies
- **art**: ASCII art logo (currently causes import error)
- **main.py**: Standalone script with minimal dependencies (only standard library)

## Modification Guidelines
- When editing the caesar function, ensure the modulo operation handles negative shifts correctly
- The output_text accumulation should happen outside the character loop
- Consider making the art import optional with try/except handling