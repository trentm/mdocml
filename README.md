A mirror/fork of mdocml from <http://mdocml.bsd.lv/>.
Is there another GH repo for this?

My immediate goal is to get nicer/cleaner HTML output for man pages.
The current HTML output via:

    $ mandoc -Thtml -Ostyle=style.css foo.1 >foo.1.html

inlines a lot more styles than I think necessary and other things

I'll call my output mode "html5". All work is in the [html5
branch](https://github.com/trentm/mdocml/tree/html5).


# html5 things to improve

- not all caps title
- try other man pages for missed styles
- [postprocess] TOC
- [postprocess] link-up embedded "foo(N)" text. See
  <http://rtomayko.github.com/ronn/ronn.1.html#LINK-INDEXES>
- [postprocess] get full "NAME" section content first sentence in the <title>

# Someday/Maybe

- <header>, <footer>
- `&#91;` and others necessary?
- decide if all the list-* styles are necessary (see style.css)
- a way to control the OS in footer
- optional OS in <title> (e.g. to get google juice and association
  for the OS).



# Dev Notes

    make mandoc
    ./mandoc -Thtml -Ostyle=style.css preconv.1 > preconv.1.html
    ./mandoc -Thtml5 -Ostyle=style.css preconv.1 > preconv.1.html5
    diff -u preconv.1.html preconv.1.html5


https://github.com/h5bp/html5-boilerplate/blob/master/index.html
