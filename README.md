# SSMF: Signalsmith's Mathfun library

This implements a few commonly-used functions (like exp/sin/sqrt) as a single plain-C header.  The goals are:

* fast (preferably tunable)
* accurate enough for audio DSP
* no dependencies, even standard-library stuff
* can be used as scalars or SIMD

The last one there is particularly interesting to me.  The idea is that the actual techniques are kinda independent of the actual types being used.  The result is a single header which acts like one big preprocessor macro - you `#define` the value types and basic operators, and it generates functions which operate on that type.  The same header can be included multiple times to define float, double, or SIMD types.

I developed it as part of writing a low-level intrinsics-based implementation for my [Linear](https://github.com/Signalsmith-Audio/linear) library, which I use for a lot of projects.  The tests are a single `.c` file which you can compile in different ways to test various configs.  It runs on scalar values (float/double).

There are more details in a big comment at the top of the [header itself](signalsmith-mathfun.h).

## License

This is licensed as [0BSD](LICENSE.txt), which is a "do whatever you want" license.
