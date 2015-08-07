Tip: Pressing Enter runs the last command.

Set breakpoint in a file at a certain line::

    breakpoint set -f [filename] -l [line]

Delete all breakpoints::

    breakpoint delete

Run::

    run [command-line arguments]

Step into function::

    si

Step out of a function::

    thread step-out

Step over function::

    n

Look at current stack variables::

    frame var

Look at a specific variable::

    frame var [varname]

Execute an expression::

    expr [expression]

Backtrace (see frames)::

    thread backtrace

Continue (until next breakpoint)::

    c

Continue (skipping [n] breakpoints)::

    c -i [n]

View contents of specific memory address::

    expr [address]    # assigns it to $[number]
    expr *(([Class]*)$[number])    -or-    *(([Class]*)[address])

Watch (break when a variable changes to specific value;
(first run program and break when variable is in scope)::

    watch set var [var_name]
    watch modify -c ‘([var_name] == [value])'
