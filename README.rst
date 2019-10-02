############
 nim-htmlcc
############
macro to use htmlgen more comfort

Examples
========
You cannot use ``htmlgen`` (stdlib in nim) macros with
more than two string clauses as following.

.. code-block:: nim

  import htmlgen

  ## IT CANNOT BE COMPILED.
  echo:
    html:
      ## You cannot write two clauses in one ``html`` or other tag macro.
      ## For example, a ``head`` macro and a ``body`` macro cannot be used
      ## in one ``html`` macro as following
      head:
        "HEAD FOO"
      body:
        "BODY BAR"

But now, you can write two clauses in one tag macro with ``htmlcc`` macro!

.. code-block:: nim

  import htmlcc

  echo:
    htmlcc html:
      htmlcc head:
        title:
          "TITLE FOO"
        meta(charset="utf-8")
      htmlcc body:
        h1:
          "TITLE FOO"
        br()
        "body bar, hogefugapiyo......"

It echos ``"<html><head><title>TITLE FOO</title><meta charset="utf-8" /></head><body><h1>TITLE FOO</h1><br />body bar, hogefugapiyo......</body></html>"``
