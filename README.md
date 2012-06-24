A mirror/fork of mdocml from <http://mdocml.bsd.lv/>.
Is there another GH repo for this?

My immediate goal is to get nicer/cleaner HTML output for man pages.
The current HTML output via:

    $ mandoc -Thtml -Ostyle=style.css foo.1 >foo.1.html

inlines a lot more styles than I think necessary and other things

I'll call my output mode "html5". All work is in the [html5
branch](https://github.com/trentm/mdocml/tree/html5).


# html5 things to improve

- <p> tags for bare content
- markdown2-style header ids:
    bufcat_id(struct html *h, const char *src) in html.c
- <section> instead of <div class="section">
- <header>, <footer>
- `&#91;` and others necessary?
- try other man pages for missed styles
- revisit CSS classes assigned
- nicer stock CSS



# Dev Notes

    make mandoc
    ./mandoc -Thtml -Ostyle=style.css preconv.1 > preconv.1.html
    ./mandoc -Thtml5 -Ostyle=style.css preconv.1 > preconv.1.html5
    diff -u preconv.1.html preconv.1.html5


https://github.com/h5bp/html5-boilerplate/blob/master/index.html
