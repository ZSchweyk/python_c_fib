```
sudo apt install pybind11-dev
```

To properly compile the cpp file and bind it with python, do the following...
```
c++ -O3 -Wall -shared -std=c++17 -fPIC $(python3 -m pybind11 --includes) fibonacci_lib.cpp -o fibonacci_lib$(python3-config --extension-suffix)
```