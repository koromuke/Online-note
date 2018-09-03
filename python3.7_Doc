# What's New In Python3.7

This article explain the new feautuer in Python3.7, cxompared to 3.6 Python 3.7 was released on June 27, 2018. For full details, see the changlog.

## Summary - Release Hilights

### New syntax featuers:
 
 -PEP 563, postponed evolution of type annotations.

Backwords ioncompatible syntax changes;

 -async and await are now reserved kewword.

### New library modules:

 -contextvars:PEP 567 - Contextr Variables
 -detaclasses:PEP 557 - Data Classes
 - importlib.resorces

### New built-in feautuers:

 -PEP 553, thew new breakpoint() function.

### Python data model improvements:

 -PEP 562, customization of access to module attributes.
 -PEP 560, core suppot dfot typing module anf generic types.
 -the insertion-order preservation nature of dict objects has been  declared to be an official part of the Python language spec.

### Significant improvement in the standard library:

 -The asyncio module has recieved new featuers, significant usability and perfomance improvements.
 -The time module gained support for functions with nanosecond resolition.

### CPython improvementation improvements:

 -Avoidung the use of ASCII as a default text encording:
  ~PEP 538, legacy C locale coercion
  ~PEP 540, forced UTF-8 runtime mode
 -PEP 552, deterministic .pycs
 -the new development runtime mode
 -PEP 565, improved DecrecationWarning handling

### C API improvements:

 -PEP539, new C API for thread- local storage

### Documentation improvements:

 -PEP 545, Python documentation translations
 -New documentation translations: Japanese, French, and Korean.

This release feautuers notable perfomance improvements in many areas. 
The Optimizations section lists them in detail.

For a list of changes that mat affecrt compatibility with previous Python releases please refer to the Porting to Python 3.7 section.

### New Featuers

PEP 563: Postponed Evalition of Annotations

The advent of type hints in Python uncoverd two glaring usability issues with the functionality of annotations added in PEP 3107 and refined further in PEP 526:

 -annotations could only use names which were already available in the current scope, in other words they didn't support forward references of any kind; and
 -annotationg source code had adverse effects on startup time of Python programs.

Both of these isseues are fixed by postponing the evalution of annotations.Instead of compiling code which executes expressions in annottations at their definition time, the compiler in annotations at their 






















