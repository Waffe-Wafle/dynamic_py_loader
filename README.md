## A simple dynamic loader classes to load and store modules and packages during runtime.

## 1. Module Controller
### The `ModuleController` class is designed to store and work with dynamically loaded module.

### Usage:

```python
from dynamic_py_loader import ModuleController
from pathlib import Path

# Load, there is no need to call resolve(),
# also object can be inited empty to be loaded later:
absolute_path = Path(__file__).parent / 'module.py'
module = ModuleController(absolute_path)

# Access module global space:
value = module.global_var

# You can also get properties and get element obviously:
module.name  # 'module'
module.path
module.get('global_var1', None)  # Default value specified

# And reload object:
module.load_self(another_path)
```
-----------------

## 2. Package Controller
### The `PackageController` class is designed to store and work with dynamically loaded package.
### It can contain modules and subpackages, also imports all from `__init__.py`.

### Usage:

```python
from dynamic_py_loader import PackageLoader
from pathlib import Path

# Load will work even for modern package without __init__.py,
# also object can be inited empty:
absolute_path = Path(__file__).parent / 'package'
package = PackageLoader(absolute_path)

# Package will contain all modules and subpackages names, you can access them as attributes.
# To access elements in __init__.py you don't need to use modulename, they are applied directly to package name.
package.init_global_var
package.module.global_var
package.subpackage.subpackaeg_module.global_var

# You can also get iterator for all elements in package namespace:
[print(elem.name) for elem in package]

# It also has analogically api as module 
package.name  # 'package'
package.path

# Some modules or subpackages can be added even if they are from other path, or 
# package can be reloaded
package.load_self()
package.load_sub_package()
package.load_module()

# You can also get by name elements of some type or get all elements:
package.get_sub_package()
package.get_module()
package.get_all_elements()  # Same list as iterator moves around
```
-----------------

## 3. Dynamic loader wrapper (PackageController)
### Just wrapper to push arguments more comfortable and with ability to load modules and packages in the same level.

### Usage:

```python
from dynamic_py_loader import PackageLoader
from pathlib import Path

absolute_path = Path(__file__).parent / 'package'
package = PackageLoader(absolute_path)

package4 = PackageLoader('./pkg4')
packages = PackageLoader('./pkg1', ['./pkg2', './pkg3'], package4)

alias = packages.pkg1.pkg1_elem
```
