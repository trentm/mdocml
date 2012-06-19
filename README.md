A mirror/fork of mdocml from <http://mdocml.bsd.lv/>.
Is there another GH repo for this?

My immediate goal is to get nicer/cleaner HTML output for man pages.
The current HTML output via:

    $ mandoc -Thtml -Ostyle=style.css foo.1 >foo.1.html

inlines a lot more styles than I think necessary and other things

I'll call my output mode "html5". All work is in the [html5
branch](https://github.com/trentm/mdocml/tree/html5).


# html5 things to improve

- html5 doctype
- no inline styles
- drop hardcoded col widths
- markdown2-style header ids
- revisit CSS classes assigned
- nicer stock CSS


# Dev Notes

    make mandoc
    ./mandoc -Thtml -Ostyle=style.css preconv.1 > preconv.1.html
