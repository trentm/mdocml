A mirror/fork of mdocml from <http://mdocml.bsd.lv/>.
Is there another GH repo for this?

My immediate goal is to get nicer/cleaner HTML output for man pages.
The current HTML output via:

    $ mandoc -Thtml -Ostyle=style.css foo.1 >foo.1.html

inlines a lot more styles than I think necessary and other things

I'll call my output mode "html5". All work is in the [html5
branch](https://github.com/trentm/mdocml/tree/html5).


# html5 things to improve

- revisit CSS classes assigned, nicer stock CSS
- ronnify:
    - <body id='manpage'>
    - <div class='mp'>
    - Lighter head and foot:
        <ol class='man-decor man-head'>
          <li class='tl'>json(1)</li>
          <li class='tc'>json tool manual</li>
          <li class='tr'>json(1)</li>
        </ol>
      before:
        <table class="head" width="100%">
        <tbody>
        <tr>
        <td class="head-ltitle">PRECONV(1)</td>
        <td class="head-vol" align="center">General Commands Manual</td>
        <td class="head-rtitle" align="right">PRECONV(1)</td>
        </tr>
        </tbody>
        </table>

    - h1 -> h2, h2 -> h3
    - from: <strong class="name">preconv</strong> &#8212; <span class="desc">recode multibyte UNIX manuals</span></div>
        to: <code>json</code> - <span class="man-whatis">(aka "jsontool") JSON love for your command line.</span>
    - from:
            <dl class="list list-tag">
            <dt class="list-tag"><strong class="flag">&#45;D</strong> <em class="arg">enc</em></dt>
            <dd class="list-tag">
            The default encoding.</dd>
            <dt class="list-tag"><strong class="flag">&#45;e</strong> <em class="arg">enc</em></dt>
            <dd class="list-tag">
            The document's encoding.</dd>
            <dt class="list-tag"><em class="arg">file</em></dt>
            <dd class="list-tag">
            The input file.</dd>
            </dl>
        to:
            <dl>
            <dt><code>-h</code>, <code>--help</code></dt><dd><p>Print this help info and exit.</p></dd>
            <dt><code>--version</code></dt><dd><p>Print version of this command and exit.</p></dd>
            <dt><code>-q, --quiet</code></dt><dd><p>Don't warn if input isn't valid JSON.</p></dd>
            </dl>
    - maybe from <pre> to <pre><code>
    - not all caps title

- try other man pages for missed styles
- TOC
- link-up embedded "foo(N)" text. See
  <http://rtomayko.github.com/ronn/ronn.1.html#LINK-INDEXES>
- get full "NAME" section content first sentence in the <title>
    - see `b` in `mdoc_root_pre`
- a way to control the OS in footer
- optional OS in <title> (e.g. to get google juice and association
  for the OS).
- <section> instead of <div class="section">
- <header>, <footer>
- `&#91;` and others necessary?



# Dev Notes

    make mandoc
    ./mandoc -Thtml -Ostyle=style.css preconv.1 > preconv.1.html
    ./mandoc -Thtml5 -Ostyle=style.css preconv.1 > preconv.1.html5
    diff -u preconv.1.html preconv.1.html5


https://github.com/h5bp/html5-boilerplate/blob/master/index.html
