# What’s New In Python 3.8
This article explains the new features in Python 3.8, compared to 3.7.

For full details, see the changelog.

Note Prerelease users should be aware that this document is currently in draft form. It will be updated substantially as Python 3.8 moves towards release, so it’s worth checking back even after reading earlier versions.
Summary – Release highlights
New Features
Parallel filesystem cache for compiled bytecode files
The new PYTHONPYCACHEPREFIX setting (also available as -X pycache_prefix) configures the implicit bytecode cache to use a separate parallel filesystem tree, rather than the default __pycache__ subdirectories within each source directory.

The location of the cache is reported in sys.pycache_prefix (None indicates the default location in __pycache__ subdirectories).

(Contributed by Carl Meyer in bpo-33499.)

Other Language Changes
A continue statement was illegal in the finally clause due to a problem with the implementation. In Python 3.8 this restriction was lifted. (Contributed by Serhiy Storchaka in bpo-32489.)
Added support of \N{name} escapes in regular expressions. (Contributed by Jonathan Eunice and Serhiy Storchaka in bpo-30688.)
New Modules
None yet.
Improved Modules
Optimizations
shutil.copyfile(), shutil.copy(), shutil.copy2(), shutil.copytree() and shutil.move() use platform-specific “fast-copy” syscalls on Linux, macOS and Solaris in order to copy the file more efficiently. “fast-copy” means that the copying operation occurs within the kernel, avoiding the use of userspace buffers in Python as in “outfd.write(infd.read())”. On Windows shutil.copyfile() uses a bigger default buffer size (1 MiB instead of 16 KiB) and a memoryview()-based variant of shutil.copyfileobj() is used. The speedup for copying a 512 MiB file within the same partition is about +26% on Linux, +50% on macOS and +40% on Windows. Also, much less CPU cycles are consumed. See Platform-dependent efficient copy operations section. (Contributed by Giampaolo Rodola’ in bpo-25427.)
The default protocol in the pickle module is now Protocol 4, first introduced in Python 3.4. It offers better performance and smaller size compared to Protocol 3 available since Python 3.0.
Removed one Py_ssize_t member from PyGC_Head. All GC tracked objects (e.g. tuple, list, dict) size is reduced 4 or 8 bytes. (Contributed by Inada Naoki in bpo-33597)
uuid.UUID now uses __slots__ to reduce its memory footprint. Note that this means that instances can no longer be weak-referenced and that arbitrary attributes can no longer be added to them.
Build and C API Changes
The result of PyExceptionClass_Name() is now of type const char * rather of char *. (Contributed by Serhiy Storchaka in bpo-33818.)

The duality of Modules/Setup.dist and Modules/Setup has been removed. Previously, when updating the CPython source tree, one had to manually copy Modules/Setup.dist (inside the source tree) to Modules/Setup (inside the build tree) in order to reflect any changes upstream. This was of a small benefit to packagers at the expense of a frequent annoyance to developers following CPython development, as forgetting to copy the file could produce build failures.

Now the build system always reads from Modules/Setup inside the source tree. People who want to customize that file are encouraged to maintain their changes in a git fork of CPython or as patch files, as they would do for any other change to the source tree.

(Contributed by Antoine Pitrou in bpo-32430.)

Deprecated
Deprecated methods getchildren() and getiterator() in the ElementTree module emit now a DeprecationWarning instead of PendingDeprecationWarning. They will be removed in Python 3.9. (Contributed by Serhiy Storchaka in bpo-29209.)

Passing an object that is not an instance of concurrent.futures.ThreadPoolExecutor to asyncio.loop.set_default_executor() is deprecated and will be prohibited in Python 3.9. (Contributed by Elvis Pranskevichus in bpo-34075.)

The __getitem__() methods of xml.dom.pulldom.DOMEventStream, wsgiref.util.FileWrapper and fileinput.FileInput have been deprecated.

Implementations of these methods have been ignoring their index parameter, and returning the next item instead.

(Contributed by Berker Peksag in bpo-9372.)

Removed
The pyvenv script has been removed in favor of python3.8 -m venv to help eliminate confusion as to what Python interpreter the pyvenv script is tied to. (Contributed by Brett Cannon in bpo-25427.)
parse_qs, parse_qsl, and escape are removed from cgi module. They are deprecated from Python 3.2 or older.
filemode function is removed from tarfile module. It is not documented and deprecated since Python 3.3.
The XMLParser constructor no longer accepts the html argument. It never had effect and was deprecated in Python 3.4. All other parameters are now keyword-only. (Contributed by Serhiy Storchaka in bpo-29209.)
Removed the doctype() method of XMLParser. (Contributed by Serhiy Storchaka in bpo-29209.)
Porting to Python 3.8
This section lists previously described changes and other bugfixes that may require changes to your code.

Changes in Python behavior
Yield expressions (both yield and yield from clauses) are now disallowed in comprehensions and generator expressions (aside from the iterable expression in the leftmost for clause). (Contributed by Serhiy Storchaka in bpo-10544.)
Changes in the Python API
The selection() method of the tkinter.ttk.Treeview class no longer takes arguments. Using it with arguments for changing the selection was deprecated in Python 3.6. Use specialized methods like selection_set() for changing the selection. (Contributed by Serhiy Storchaka in bpo-31508.)
A dbm.dumb database opened with flags 'r' is now read-only. dbm.dumb.open() with flags 'r' and 'w' no longer creates a database if it does not exist. (Contributed by Serhiy Storchaka in bpo-32749.)
The doctype() method defined in a subclass of XMLParser will no longer be called and will cause emitting a RuntimeWarning instead of a DeprecationWarning. Define the doctype() method on a target for handling an XML doctype declaration. (Contributed by Serhiy Storchaka in bpo-29209.)
A RuntimeError is now raised when the custom metaclass doesn’t provide the __classcell__ entry in the namespace passed to type.__new__. A DeprecationWarning was emitted in Python 3.6–3.7. (Contributed by Serhiy Storchaka in bpo-23722.)
The cProfile.Profile class can now be used as a context manager. (Contributed by Scott Sanderson in bpo-29235.)
shutil.copyfile(), shutil.copy(), shutil.copy2(), shutil.copytree() and shutil.move() use platform-specific “fast-copy” syscalls (see Platform-dependent efficient copy operations section).
shutil.copyfile() default buffer size on Windows was changed from 16 KiB to 1 MiB.
PyGC_Head struct is changed completely. All code touched the struct member should be rewritten. (See bpo-33597)
Asyncio tasks can now be named, either by passing the name keyword argument to asyncio.create_task() or the create_task() event loop method, or by calling the set_name() method on the task object. The task name is visible in the repr() output of asyncio.Task and can also be retrieved using the get_name() method.
The mmap.flush() method now returns None on success and raises an exception on error under all platforms. Previously, its behavior was platform-depended: a nonzero value was returned on success; zero was returned on error under Windows. A zero value was returned on success; an exception was raised on error under Unix. (Contributed by Berker Peksag in bpo-2122.)
The function math.factorial() no longer accepts arguments that are not int-like. (Contributed by Pablo Galindo in bpo-33083.)
uuid.UUID now uses __slots__, therefore instances can no longer be weak-referenced and attributes can no longer be added.
CPython bytecode changes
The interpreter loop has been simplified by moving the logic of unrolling the stack of blocks into the compiler. The compiler emits now explicit instructions for adjusting the stack of values and calling the cleaning up code for break, continue and return.

Removed opcodes BREAK_LOOP, CONTINUE_LOOP, SETUP_LOOP and SETUP_EXCEPT. Added new opcodes ROT_FOUR, BEGIN_FINALLY, CALL_FINALLY and POP_FINALLY. Changed the behavior of END_FINALLY and WITH_CLEANUP_START.

(Contributed by Mark Shannon, Antoine Pitrou and Serhiy Storchaka in bpo-17611.)

Added new opcode END_ASYNC_FOR for handling exceptions raised when awaiting a next item in an async for loop. (Contributed by Serhiy Storchaka in bpo-33041.)
