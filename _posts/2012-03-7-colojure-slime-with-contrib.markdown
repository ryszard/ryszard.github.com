---
layout: default
title: Slime for Clojure with slime-contrib
comments: true
---

One of the big differences between how Slime is supported in Clojure and in Common Lisp is that in Clojure the party responsible for loading elisp code is Leiningem (not Emacs). [Swank-clojure](https://github.com/technomancy/swank-clojure) includes Slime's code as a payload, and when you call it is put in your load-path and loaded. This makes a lot of things easier: for example, you don't have to worry about Clojure and Slime running out of sync, and you can even use different Swank versions for different projects.

Unfortunately, if you are used to programming in Common Lisp with Slime, you will soon notice that one important thing is missing. The elisp payload included with swank-clojure contains just vanilla slime, without any contrib package. For me, some of them absolutely essential. I can hardly imagine lisp programming without being able to get Slime to complete p-c-r&#060;TAB&#062; to "partial-completion-rocks." Another thing that a lot of people use is fuzzy completion.

Normally, it would be very easy to add these things. However, this situation is a bit unusual – you don't have normal access to the elisp code, and you need a specific version of the slime contribs.

So, how to get Clojure Slime with all the bells and whistles working?

Install [swank-clojure](https://github.com/technomancy/swank-clojure) using leiningen

<script src="https://gist.github.com/1998042.js"> </script>

and get [clojure-mode](https://github.com/technomancy/clojure-mode) to a directory in your load-path.

<script src="https://gist.github.com/1998186.js"> </script>

Download the contrib files you are interested from [here](https://github.com/technomancy/slime/tree/master/contrib) to your load-path. This is a Slime fork maintained by the same person as clojure-mode, so it's guaranteed to keep working.

<script src="https://gist.github.com/1998059.js"> </script>

Finally, add a hook to load the contrib stuff.

<script src="https://gist.github.com/1998069.js"> </script>

Note that you cannot add it to clojure-mode itself, as at that point Slime code may not be available yet.
