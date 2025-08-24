# jsonlutils

A lightweight Python library for working with **JSONL (JSON Lines)** and **JSON** files.  
Provides easy conversion, validation, and utility functions.

## ✨ Features

- Convert JSONL → JSON (with metadata)
- Convert JSON → JSONL
- Validate JSONL consistency
- Extract keys from JSONL
- Get statistics (average values, counts, etc.)

## 📦 Installation

```bash```
pip install jsonlutils

import jsonlutils as ju

## Functions 🚀 Quick Start

# Convert JSONL → JSON
Take in a JSONL file and convert it to a JSON file and output it to the specified output file
return the json dictionary object
Parameters:
input_file: str - the path to the input JSONL file
output_file: str - the path to the output JSON file
json_indent: int - the number of spaces to use for indentation in the output JSON file
jsonl_start_index: int - the starting index of the JSONL lines to include in the output JSON file
jsonl_end_index: int - the ending index of the JSONL lines to include in the output JSON file
print_error_logs: bool - whether to print error logs for invalid JSON lines in the input file
print_conversion_summary: bool - whether to print a summary of the conversion process
return_json_dict: bool - whether to return the JSON dictionary object
sort_data: bool - whether to sort the data array in the output JSON file
sort_data_key: str - the key to sort the data array by if sort_data is True
sort_descending: bool - whether to sort the data array in descending order if sort_data is

returns JSON dictionary unless parameter set to false

Expected output format returned and/or written to file:
{
    "config": {
        "name": "Converted Dataset",
        "Original_Data_set_filename": "input.jsonl",
        "number_of_objects": "100",
        "number_of_objects_in_original_file": "150"
    },
    "data": [
        {...}, 
        {...}
    ]
}

Base Usage
ju.convert_jsonl_to_json("data.jsonl", "out_data.json")

# Validate consistency
Checks if all JSON objects in a JSONL file have the same keys, and that every line is valid JSON
Parameters:
input_file: str - the path to the input JSONL file
print_error_messages: bool - whether to print error messages for inconsistent keys or invalid JSON lines

returns true if all json objects have the same keys

is_consistent = ju.check_jsonl_is_consistent("data.jsonl")
print("Consistent:", is_consistent)

# Get keys

Goes through a JSONL file and finds all unique keys in the JSON objects
Parameters:
input_file: str - the path to the input JSONL file
print_error_message: bool - whether to print error messages for invalid JSON lines

returns: set - set of all unique keys found in the JSON objects

Usage:
keys = ju.find_all_jsonl_keys("data.jsonl")
print("Keys found:", keys)

# Get json objects through yield
Reads a JSONL file and yields JSON objects
Parameters:
input_file: str - the path to the input JSONL file

Yields: dict - the next JSON object in the file

get_json_objects_from_jsonl_yield("data.jsonl")

#Get list of json objects
Reads a JSONL file and returns a list of JSON objects
Parameters:
input_file: str - the path to the input JSONL file

Returns: list - a list of JSON objects in the file

Usage:
json_list = get_list_of_json_objects_from_jsonl("data.jsonl")

# Get average numeric value of jsonl
Reads a JSONL file and returns the average value of a specified key
Parameters:
input_file: str - the path to the input JSONL file
key: str - the key to calculate the average value for, needs to be numeric
print_error_messages: bool - whether to print error messages for invalid JSON lines or non-numeric values

Returns: float - the average value of the specified key

Usage:
average_val = get_average_value_of_jsonl_value("data.jsonl", "num_key")

# Get number of valid json objects in jsonl
Reads a jsonl object and returns number of valid json and total lines in the file
parameters:
input_file - file to read
    
returns int, int - returns number of objects and then total lines

Usage:
get_number_of_json_objects_in_jsonl("data.jsonl")

# Convert JSON → JSONL
Takes a json objects and converts it to a jsonl file by taking an array of keys from the json object
and then writing each object in the data array to a new line in the jsonl file with all other keys being consistent
Parameters:
input_file: str - the path to the input JSON file
output_file: str - the path to the output JSONL file
data_key_array: list - the keys to extract from each object in the data array and write to the jsonl file
    
Returns: bool - True if the conversion was successful, False otherwise

Usage:
ju.convert_json_to_jsonl("data.json", "data.jsonl", data_key="data")

📂 Project Structure
jsonlutils/
│
├── src/jsonlutils/        # Core library code
│   ├── __init__.py
│   └── converter.py
│
├── tests/                 # Unit tests
│   └── test_converter.py
│
├── pyproject.toml         # Build metadata
├── README.md              # This file
├── LICENSE                # MIT license
└── .gitignore

📄 License

MIT License. See LICENSE for details.

Contributing

Fork the repo
Create a new branch (feature/my-feature)
Commit your changes
Push the branch and open a Pull Request
