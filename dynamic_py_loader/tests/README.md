### Tests Tree
```text
tests/
├── pkg1/
│   ├── pkg1_sub_pkg/
│   │   ├── __init__.py
│   │   └── source_1_1.py
│   ├── __init__.py
│   └── source_1.py
├── коська/
│   ├── подкоська/
│   │   ├── __init__.py
│   │   └── sub_cat_module.py
│   ├── __init__.py
│   └── cat_module.py
├── __init__.py
├── direct_module.py
├── README.md
└── unittests.py
```

### Every module contains a dictionary named `[UPPERCASE_MODULE_NAME]_GLOBAL`:

```python
# Example of contents in each module:
# [UPPERCASE_MODULE_NAME]_GLOBAL = {
#     'key': 'value'
# }
SOURCE_1_1_GLOBAL = {
    'key': 'value'
}

SOURCE_1_GLOBAL = {
    'key': 'value'
}

SUB_CAT_MODULE_GLOBAL = {
    'key': 'value'
}

CAT_MODULE_GLOBAL = {
    'key': 'value'
}

DIRECT_MODULE_GLOBAL = {
    'key': 'value'
}

```
