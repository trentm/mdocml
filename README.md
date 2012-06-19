A mirror/fork of mdocml from <http://mdocml.bsd.lv/>.
Is there another GH repo for this?

My immediate goal is to get nicer/cleaner HTML output for man pages.
The current HTML output via:

    $ mandoc -Thtml -Ostyle=style.css foo.1 >foo.1.html

inlines a lot more styles than I think necessary.

I'll call my output mode "html5".

# Dev Notes

    make mandoc
    ./mandoc -Thtml -Ostyle=style.css preconv.1 > preconv.1.html
    ./mandoc -Txhtml -Ostyle=style.css preconv.1 > preconv.1.xhtml
