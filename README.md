# PracticePythonProjects

Exercises Taken from [learn by example](https://learnbyexample.github.io/practice_python_projects/calculator/exercises.html)

## Python CLI Application
Project specs were to write a command line application using Python's sys and argparse modules. The last example given was to evaluate an expression from stdin. User could either have the expression solve, give a floating point output precision amount, change the format of the expression to binary, octal or hexadecimal format, and a verbose mode that shows both the input and output. Code specs below--

## Python Calculator (Credit to Sundeep Agarwal)
```
# py_calc.py
import argparse, sys

parser = argparse.ArgumentParser()
parser.add_argument('ip_expr', nargs='?',
                    help="input expression to be evaluated")
parser.add_argument('-f', type=int,
                    help="specify floating point output precision")
parser.add_argument('-b', action="store_true",
                    help="output in binary format")
parser.add_argument('-o', action="store_true",
                    help="output in octal format")
parser.add_argument('-x', action="store_true",
                    help="output in hexadecimal format")
parser.add_argument('-v', action="store_true",
                    help="verbose mode, shows both input and output")
args = parser.parse_args()

if args.ip_expr in (None, '-'):
    args.ip_expr = sys.stdin.readline().strip()

try:
    result = eval(args.ip_expr)

    if args.f:
        result = f'{result:.{args.f}f}'
    elif args.b:
        result = f'{int(result):#b}'
    elif args.o:
        result = f'{int(result):#o}'
    elif args.x:
        result = f'{int(result):#x}'

    if args.v:
        print(f'{args.ip_expr} = {result}')
    else:
        print(result)
except (NameError, SyntaxError):
    sys.exit("Error: Not a valid input expression")
```

## Assigment Exercises:
Modify the scripts such that these additional features are also implemented.

If the output is of float data type, apply .2f precision by default. This should be overridden if a value is passed along with -f option. Also, add a new option -F to turn off the default .2f precision.

Use math module to allow mathematical methods and constants like sin, pi, etc.

If the input expression has a sequence of numbers followed by ! character, replace such a sequence with the factorial value. Assume that input will not have ! applied to negative or floating-point numbers. Or, you can issue an error if such numbers are detected.
