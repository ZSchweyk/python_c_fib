Outline
-
This code allows cpp functions to be called from python, showing how to integrate cpp's high speed in a python codebase. I implemented fibonacci in quite possibly the worst way (no memoization) just to more easily compare the speed of both cpp and python.

Setup Instructions
-
(Optional) Create and activate a virtual environment

Install necessary python libraries (just pybind11 in this case) with: `pip install -r requirements.txt`

Install pybind11-dev with: `sudo apt install pybind11-dev`

Compile a linked library file from `fibonacci_lib.cpp` and properly bind it to python with:
```
c++ -O3 -Wall -shared -std=c++17 -fPIC $(python3 -m pybind11 --includes) fibonacci_lib.cpp -o fibonacci_lib$(python3-config --extension-suffix)
```
After running that command, you should see a file called `fibonacci_lib.cpython-310-x86_64-linux-gnu.so`

Then run `fibonacci_from_cpp.py` with: `python3 fibonacci_from_cpp.py`

Summary
-
On my machine, running the following with `n=50` took
* `python3 fibonacci.py`: 43 minutes
* `./fibonacci` (compile with `g++ fibonacci.cpp -o fibonacci`): 1.82 minutes
* `python3 fibonacci_from_cpp.py`: 2.23 minutes
