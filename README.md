In this README file, I want to talk about the task that needed to be completed, my solution is in the files rationl.h and .cpp.

Condition

In C++, there are many built-in data types for working with integer arithmetic and arithmetic on floating-point numbers.
However, when calculating over the latter, rounding errors are possible, which can accumulate in complex (consisting of many operations) calculations.
If rounding cannot be avoided when working with irrational numbers, then in programs that require manipulation only with rational numbers, all calculations can be reduced to exact integer arithmetic.
This is exactly what you have to do in this task.

Implementation Details

It is necessary to implement a class to work with Rational numbers.
A rational number is represented by two mutually simple integers - the numerator and the positive denominator.
This invariant must be maintained when performing any operations on objects of the Rational class. The public interface of the class must include:

The default constructor that initializes a number to zero;
An implicit constructor for converting from integers (the following code should work Rational x = 5;). Don't forget to add a comment // NOLINT (see comments);
Constructor of two integers (numerator and denominator). At the same time, it is not guaranteed that the numbers are mutually prime and nonzero (more on this later);
The GetNumerator() and GetDenominator() methods, which return the numerator and denominator, respectively;
The SetNumerator(int) and SetDenominator(int) methods that set the numerator and denominator to the required values;
Binary arithmetic operations (+, -, /, *) and their assignment versions (+=, -=, /=, *=);
Unary operations (+, -), as well as prefix and postfix increments and decrements (++, --);
Comparison operations;
Input from stream and output to stream operations (>>, <<);
When you output a number to the stream, you must output it as an irreducible fraction in the format <numerator>/<denominator> or <numerator> if the denominator is 1.
The input is in the same format (but the fraction at the input is not necessarily irreducible).

Example:
Rational x = 5; // fraction 5/1
std::cout << x; // output: 5
x.SetDenominator(15); // fraction 1/3 (5/15 decreased)
std::cout << x; // output: 1/3
std::cin >> x; // input: 14/-6, fraction: -7/3 (common multiplier 2; denominator > 0)

Division by 0 When dividing by 0 (in the division operation or when setting the denominator to 0), the program should report an error. For these purposes, C++ has an exception mechanism.
The exception is an object of some class that is inherited from the standard error class of the C++ library.
If everything is not clear now, then it's ok, if everything is not clear before the test or exam - you have problems.
The RationalDivisionByZero error class is written for you, you only need to report the error using the string at the moment when the division by zero occurs: throw RationalDivisionByZero{};
