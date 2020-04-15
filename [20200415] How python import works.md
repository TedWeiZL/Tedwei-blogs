# A rough breakdown of python import function

Here is what happens when we run the following code
```python
import module1
```
### 1.  Search
A module is a ```.py``` file containing legitimate python code. Therefore the first step for the compiler is to find where the file ``` module1.py``` is. It searches for this file in the system's ```PATH``` variable and the current directory.
We can see all our ```PATH``` variables by running the following script in python.

```python
import sys
sys.path
```
This code will return a list of paths represented by strings. In order to run a successful import, our file ```module1.py``` must be saved in one of the paths.
Additionally, we can add a new path to the ```path``` variable by using
```python
sys.path.append(your path)
```
This adds a new element in the ```sys.path``` list. However, this operation is only **temporay**, the new element will be erased once the execution of this program is complete.

### 2. Creating namespace for the imported module
Each module has its own ***private symbol table***, which serves as the global symbol table for all objects defined in the module. Thus, a module creates a separate namespace, as already noted.

### 3. Run the code!
Last but not least, it will run the ```module1.py``` code! If we don't want a certain part of our script to be run when importing it, we should put these lines of code under the ```if __name__ == '__main__' : ``` clause.

## Important to take note:
Since our imported module has its own ***private symbol table***, it does not recognize any variable name from the caller. 
For example, if we have already imported the ```numpy``` module, and if our new module to be imported also uses any numpy function, it has to import ```numpy``` again!

if our ```module1.py``` looks like the following:
```python
a=numpy.zeros((3,3))
.....
```
if ```module1.py``` does not have the ```import numpy``` statement (just like written above), then an error message will be returned because ```numpy``` cannot be recognized by ```module1.py``` without importing it again!
