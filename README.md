# PicoVector
Minimal vector classes for C++ and JavaScript in less than a hundred lines of code.

### Usage
These files have a similar structure: they contain one class representing the vector and some operators or extension methods. They are (not meant to be) efficient, but they should be easy to use and have a somewhat uniform interface.

#### C++
[vectorND.h](vectorND.h) contains, as the name suggests, a vector class for N-dimensional vectors. It inherits from `std::array` and takes two template parameters: the size of the vector N and the numeric carrier type T. Overloads provide the majority of the functionality, with the handy `norm`, `normalized`, `bounds`, and `clip` methods also available. 

You can implement most functionality not covered by these with `map`, `partial`, or `reduce`.\
`map` applies a function to every vector element.\
`partial` takes a binary operation and returns a function you can apply to a second vector.\
`reduce` reduces the vector to something else, similar to fold in functional languages or `std::accumulate` in C++.

#### JavaScript
[vector2D.js](vector2D.js) provides a vector class with some functionality unique to 2D vectors like `angle` and `normal`. JS doesn't have operator overloading, so all operators are implemented as methods. To not completely kill performance, these methods do not use `map`, `partial`, and `reduce` for their implementation, though this makes for a [femto-sized implementation](https://gist.github.com/Adam-Vandervorst/5c1da4806aca1cdb205ebce99aeef448).

### Context
I found myself repeatedly re-implementing basic vector functionalities in various languages. I didn't want to explode compilation time or program size, and performance was not paramount. This repository tries to remedy that by being single-file and reasonably safe.

I have another 'pico' repository, [PicoStaticServer](https://github.com/Adam-Vandervorst/PicoStaticServer), which provides a minimal testing utility for static sites.

**Fun fact:**
You won't get hired if you write macros like the one I wrote in C++.
