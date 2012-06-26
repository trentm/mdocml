A mirror/fork of mdocml from <http://mdocml.bsd.lv/>.
Is there another GH repo for this?

My immediate goal is to get nicer/cleaner HTML output for man pages.
The current HTML output via:

    $ mandoc -Thtml -Ostyle=style.css foo.1 >foo.1.html

inlines a lot more styles than I think necessary and other things

I'll call my output mode "html5". All work is in the [html5
branch](https://github.com/trentm/mdocml/tree/html5).


# html5 things to improve

- smartos-isms?
    - "ATTRIBUTES" table is completely broken with `mandoc`. Sigh.

- BUG: why is "make testchmod" broken!?
    - man_html.c -> need to do all the same fixes
- cli:
    - man5 foo.1 > foo.1.html    # single page
    - options for fragment
    - options a la ronn for style
    - multi page:
        man5 /usr/share/man -o ./man-output/


- static html index.html: group by section:

    [ <filter>... ]     <!-- filter down the list -->

    # man1

    aaa         blah blah blah
    bbb         blah blah blah

    # man2

    ...
- proj layout:
    - remove unused C, etc.
    - move mdocml to src dir (perhaps have a *dep* on this?)
    - bin/man5  # node.js dep
- proj name: man2web, man5 (fav), heman (Html E??? Man)
    - search for man5 usage
- single man page improvements
    - id's:
        - disallow leading '-'s: file://localhost/Users/trentm/tm/mdocml/mdoc.7.html#--nm
        - disallow trailing '-'s
    - need to trim empty <p>, e.g. in mdoc.7.html after "Document preamble and NAME section macros"
    - table first column width: see tables at "Document preamble and NAME section macros" in mdoc.7.html
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
