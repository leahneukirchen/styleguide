# Christian Neukirchen's C Style Guide

You may not like all rules presented here, but they work very well for
me and have helped producing high quality code.  Everyone is free to
code however they want, write and follow their own style guides, but
when you contribute to my code, please follow these rules:

This guide does not explain how to write good C code,
but merely how to format it.

## Formatting:

* Use ASCII (UTF-8 is ok in comments, if you have to).

* Use Unix-style line endings.  On the last line of the file, too.

* Use lowercase file names, use `.c` and `.h` extensions.

* Write valid C99.  Target POSIX.1-2008 as a base line.

* Use 1 tab for each level of indentation, 4 spaces for half-indentation.

* Keep lines fewer than 80 characters, with 8 space tabs.

* Do not use tabs for aligning, only for indentation.
  Do not use tabs in the middle of the line.
  Do not align variable names in declarations,
  use one space between type and name.
  Do not align wrapped function calls, half-indent instead.

* Use K&R indentation:
  * `{ }` of the function are in column 1.
  * `{ }` of control structures start in the same line.
    Closing and opening braces go on the same line as the else.
  * Indent case deep as switch.

* Use ANSI function declarations only.

* Function names start in column 1, types go in the line before.

* Avoid `{ }` around single statements.

* Use `{ }` consistently in if/else-if/else when one branch uses it.

* For dangling else, use `{ }` around the outer if:

		if (bar) {
			if (foo)
				foo();
			else
				notfoo();
		}

* Use spaces around assignments and comparisons,
  after keywords, commas, colons and semicolons,
  around `{` and before `}`, and around `? :`.

* No not use a space between function name and arguments.

* No spaces after `(`, `[` and before `]`, `)`.

* No spaces after unary operators.

* Use semantic spaces around operators, e.g. write `x * y`, `8*x + 6*y`.

* Indent labels in column 1.  (Exception: labels belonging to a
  switch-case are indented like the case.)

* Use an empty line after local variable declarations.

* Use an empty line before the return statement of a function (unless it
  only has one line), and an empty line between functions.

* Don't use `( )` around the argument of return.

* Use empty lines to break up a long functions into logical paragraphs.

* Break lines after `&&` and `||`, not before.

* Avoid trailing whitespace.

* The pointer star belongs to the variable, not to the type.
  Write `char * strdup(char *str)`.

* Write casts like `(char *)foo`.  Do not use a space after a cast.

* Don't use parentheses after sizeof, unless its a type, then use a
  space between: `sizeof buf` and `sizeof (struct foo)`.
  Prefer sizeof with variable names.

* Do not cast `(void *)`.

* Use `<stdint.h>` and its types freely.

* Use `size_t` for array indices and string lengths.

* Order `#include` alphabetically in three blocks:
  * `<sys/...>`
  * `<...>`
  * `"..."`.

* Put each statement on its own line.
  Exception: short guards ala `if (...) break;` or `if (...) goto fail;` are ok.

* Declare functions `static` when they are only used in this translation unit.

## Idioms:

* Using the return value of `=` is ok.

* Use `while (1) ...` for infinite loops.

* Initialize zeroed structs using `= { 0 }`.

* Prefer `x+i` over `&x[i]`.

* Prefer `i++` over `++i`.

* Do not use `NULL`.  Use `0` for null pointers.
  Remember to use `(char *)0` as a sentinel for execl(3).

* Check null pointers by truth: `if (foo) ...`

* Avoid superfluous comparison to 0.
  * Exception:  Use `== 0` when 0 is the successful result, e.g.
    `strcmp(a, b) == 0`, `access(file, F_OK) == 0`, `regexec(...) == 0`.
  * Do not use `!strcmp(a, b)`.
  * Use `if (!p) ...` to check whether `p` is a null pointer.

* Don't use Yoda comparison (`0 == x`).

* Use a plain `;` on a line of itself for the empty instruction.

* Avoid `typedef` to name structs.

* Use `typedef` to name function pointers.

* Only initialize variables when it is sensible.

* Use `int` variables to store boolean values in general.

* Avoid forward declarations unless indispensable.
  Let `main` be the last function in code.

## Naming:

* The length of an identifier determines its scope.

* Respect POSIX namespaces: http://port70.net/~nsz/c/posix/reserved.txt
  Do not use `_t` postfix for types.

* Use `snake_case` for functions, variables, and types.

* Use `SCREAMING_SNAKE_CASE` for macros.

* Use `Xflag` for the value of the command line flag `-X`.

* Use a postfix `o` to mark output parameters.

* Use a consistent prefix for all global names in a library.

## Comments:

* Comments longer than a word are capitalized and use punctuation.
  Use two spaces after periods.

* Write single line comments like this:

		/* foo */
		// C++ style is also ok.

* Use at least two spaces before end-of-line comments in a code line.

* Write multi-line comments like this:

		/*
		 * Important comments
		 * at the beginning of the file.
		 */

		/* Inline comments
		   that can span
		   multiple lines. */

* Avoid superfluous comments.

## The rest:

* Avoid long functions.

* Avoid long parameter lists.

## General:

* Do not mutate arguments unless that is the purpose of the function.

* Keep the code simple.

* Don't overdesign.

* Don't underdesign.

* Avoid bugs.

* Read other style guides and apply the parts that don't dissent with
  this list.

* Be consistent.

* Use common sense.
