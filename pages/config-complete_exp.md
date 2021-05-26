---
title: Docs - Config Examples
permalink: /config-complete_exp.html
redirect_from:
  - /docs/config-complete_exp.html
  - /docs/config-complete_exp.shtml
created_at: 1999-04-06
last_modified_at: 2014-12-23 22:50:09 +0100
---

# Complete Examples

In order to illustrate the *boxes* configuration language described in the previous chapters, we now look at the source
code of two complete box designs, one simple and one more complex.

In addition to the examples shown here, please refer to the [official boxes config
file](https://github.com/{{ site.github }}/blob/master/boxes-config){:target="_blank"} for tons more.

{%- comment %}  TODO simply refer to config file, add best practices section instead {% endcomment -%}

## Simple Example

    BOX simple
    
        sample
            ++++++++++++
            +          +
            ++++++++++++
        ends
    
        shapes {
            n("+")  s("+")  e("+")  w("+")
           nw("+") ne("+") se("+") sw("+")
        }
    
        elastic (n,s,e,w)
    
    END simple


## Complex Example

    BOX tjc
    
        author   "John Doe <john@doe.com>"
        revision "1.1"
        revdate  "July 16, 1999 (Friday, 18:55h)"
        created  "April 02, 1999 (Friday, 19:26h)"
    
        Sample
            static char *foo (const int a, const int b)
            /*
             *  Do the foo on the bar and around again.
             *
             *      a     number of doodlefrobs
             *      b     barfoo mode (0 == off)
             *
             *  Memory will be allocated for the result.
             *  Should only be called for lines of length > 0;
             *
             *  RETURNS:  Success: Pointer to result line
             *            Error:   -1   (e.g. frobs depleted)
             *
            * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
             */
            {
                static char temp ....
                int ii;          ....
        ends
    
        indent "none"                 # alternatives: "box", "text"
    
        shapes {
            wnw ("/*")
            w   (" *")
            sw  ("* ", " *")
            ssw ("*", "/")
            s   (" *", "  ")
        }
    
        elastic (s, w)
    
        delimiter ?"
    
        replace "\*/" with "*\/"      # quote closing comment tags
        reverse "\*\\/" to "*/"
    
        padding {
            left 2
            vertical 1
        }
    
    END tjc

Note the `SAMPLE` block of the latter example. It shows much more than just the box itself, trying to give the user an
impression of what the box would look like if used in reality. We only need half the backslashes in the `REVERSE` and
`REPLACE` statements because we use `delimiter` to change the escape character from backslash to question mark.
