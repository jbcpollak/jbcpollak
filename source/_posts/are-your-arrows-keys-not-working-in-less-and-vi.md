title: Are your arrows keys not working in less and vi?
tags:
  - iterm
  - less
  - linux
  - mac
  - OS X
  - terminal
  - vi
id: 54
categories:
  - Tech
date: 2007-11-05 18:58:40
---

I've had this problem sporadically with iTerm on my Mac, and I seem to remember this happening recently on my Linux machines as well. If you have this problem, try this:

`$ export TERM=linux`

If this works, on a Mac you can set it in your .profile:

<pre>
if [ "${TERM_PROGRAM}" == "iTerm.app" ]
then
export TERM=linux
fi
</pre>

On Linux, you can do the same, but leave out the if and just do the export line.
