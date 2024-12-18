# Tree Maker

A simple Python package that creates a directory and file structure from a given JSON or Python object.

## Installation

You can install the package using `pip`:

```bash
pip install easy-tree-maker
```

## Usage

You can use the `TreeMaker` class to create directories and files based on a JSON or Python structure.

### Example with Python object:

```python
from easy_tree_maker.core import TreeMaker

# Define the tree structure as a Python object
tree_structure = [
    {
        "type": "directory",
        "name": "TestProject",
        "contents": [
            {"type": "file", "name": "README.md"},
            {"type": "directory", "name": "src", "contents": [
                {"type": "file", "name": "app.py"}
            ]}
        ]
    }
]

# Create the tree with the Python object structure
tree_maker = TreeMaker(tree_structure, is_json=False)
tree_maker.create_tree(root_path="./TestDirectory")
```

### Example with JSON string:

```python
import json
from easy_tree_maker.core import TreeMaker

# Define the tree structure as a JSON string
tree_structure_json = json.dumps([
    {
        "type": "directory",
        "name": "TestProject",
        "contents": [
            {"type": "file", "name": "README.md"},
            {"type": "directory", "name": "src", "contents": [
                {"type": "file", "name": "app.py"}
            ]}
        ]
    }
])

# Create the tree with the JSON string structure
tree_maker = TreeMaker(tree_structure_json, is_json=True)
tree_maker.create_tree(root_path="./TestDirectory")
```

### Example with JSON file:

If you have a JSON file containing the tree structure, you can use it as input:

```python
from easy_tree_maker.core import TreeMaker
import json

# Load the tree structure from a JSON file
with open('tree_structure.json', 'r') as f:
    tree_structure_json = f.read()

tree_maker = TreeMaker(tree_structure_json, is_json=True)
tree_maker.create_tree(root_path="./TestDirectory")
```

## CLI Usage

You can also use the command-line interface (CLI) to create the tree structure from a JSON file or string.

To use the CLI, run:

```bash
easy_tree_maker path_to_json_file_or_string --root /path/to/create/tree
```

### Example:
```bash
easy_tree_maker tree_structure.json --root /tmp/test_tree
```

This will read the JSON file `tree_structure.json` and create the directory and file structure in `/tmp/test_tree`.