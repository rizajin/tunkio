# Binary to Header File Converter

This program is a command-line tool that reads a binary file and converts its content into a C++ header file, which can be included in your project. The output header file contains an array of `uint8_t` representing the binary data from the input file.

## Usage

program_name <input_file> [output_file]


### Parameters

- `<input_file>`: Path to the input binary file (required).
- `[output_file]`: Path to the output header file (optional). If not provided, the default name 'output_header.h' will be used.

### Options

- `-h`, `--help`: Display the help message and exit.

## Example

program_name example.bin example_data.h


This command reads the binary data from `example.bin` and creates a header file named `example_data.h` containing the data as an array of `uint8_t`.

## Executable

This program is published as an 64bit Windows executable only for now.  
And here are the hashes for checking the validity,  
SHA1: de1af912d2e03b61a233aca86a63b1e8bc499b2b  
SHA256: 53a60af0359a27637393fe4c59237e86b10c0e160500afdd2ee08e1479d4e3a2
