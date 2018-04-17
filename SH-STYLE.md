# Leah Neukirchen's Shell Style Guide

You may not like all rules presented here, but they work very well for
me and have helped producing high quality code.  Everyone is free to
code however they want, write and follow their own style guides, but
when you contribute to my code, please follow these rules:

This guide does not explain how to write good shell code,
but merely how to format it.

## Formatting:

* Use ASCII (UTF-8 is ok in comments, if you have to).

* Use Unix-style line endings.  On the last line of the file, too.

* If you use a file extension, use `.sh`.
  Don't use a file extension for executable scripts.

* In general, write valid POSIX /bin/sh.  Target POSIX.1-2008 as a base line.
  Avoid bashisms like `[[`, `[ x == y ]`, `${::}`, `${//}` and arrays.
  Do not nest `${#}` and `${%}`.

* Use 1 tab for each level of indentation, 4 spaces for half-indentation.

* Keep lines fewer than 80 characters, with 8 space tabs.

* Do not use tabs for aligning, only for indentation.
  Do not use tabs in the middle of the line.

* Function names start in column 1.  Do not use the function keyword.

	myfoo() {
		...
	}

* No space between function name and arguments.

* Use empty lines to break up a long functions into logical paragraphs.

* Break lines after `&&` and `||`, do not use explicit line
  continuations with `\` then.

* Put `do` and `then` into the same line as the loop:

	for f in *; do
		...
	done

	if [ ... ]; then
		...
	fi

* Don't indent switch cases:

	case ... in
	foo)
		...
		;;
	bar)
		...
		;;
	esac

* Never use backticks, always use `$()`.

* Avoid trailing whitespace.

## Idioms:

* Use `while :; do ...; done` for infinite loops.

* Use a plain `:` on a line of itself for the empty command.

* Always quote variables that contain external data.

* Prefer blocks over subshells for plain grouping.

* Prefer `$(( ... ))` over expr(1).

* Prefer `for arg;` over `for arg in "$@";`.

* Don't use echo (except for the most trivial uses), prefer printf.

* Never use `[ "x$foo" = x ]`.

* Use `getopts` to parse command line flags.

## Naming:

* The length of an identifier determines its scope.

* Use lowercase variables for local scope.

* Use `SCREAMING_SNAKE_CASE` for exported variables.

## Comments:

* Comments longer than a word are capitalized and use punctuation.
  Use two spaces after periods.

* Use at least two spaces before end-of-line comments in a code line.

* Avoid superfluous comments.

## The rest:

* Avoid long functions.

* Avoid long parameter lists.

## General:

* Keep the code simple.

* Don't overdesign.

* Don't underdesign.

* Avoid bugs.

* Read other style guides and apply the parts that don't dissent with
  this list.

* Be consistent.

* Use common sense.
