---
layout: post
title: "[GSoC16] Week 10 update"
date: 2016-08-01 13:30:00
category: gsoc16
---

I'm at the final stage of my GSoC project, which is writing a `coafile` editor for the Eclipse plug-in I've [been working on](http://sheikharaf.me/gsoc16/gsoc-16-with-coala.html).
After reading a lot of articles and tutorials I've finally settled on how to go about writing the editor.

To implement the editor I'll be extending the
[`FormEditor`](http://help.eclipse.org/kepler/index.jsp?topic=%2Forg.eclipse.platform.doc.isv%2Freference%2Fapi%2Forg%2Feclipse%2Fui%2Fforms%2Feditor%2FFormEditor.html)
class. This approach is helpful because it lets you add one or more [`FormPage`](http://help.eclipse.org/kepler/index.jsp?topic=%2Forg.eclipse.platform.doc.isv%2Freference%2Fapi%2Forg%2Feclipse%2Fui%2Fforms%2Feditor%2FFormPage.html)
as well as a [`StructuredTextEditor`](https://eclipse.org/webtools/wst/components/sse/designs/EditorSelection.html)
to view the raw text file.

Next I'll be using the [Eclipse SWT](https://www.eclipse.org/swt/) to implement the GUI of the `FormPage`.
It will look something like this:

![](/images/coafile-editor-eclipse-plugin.png)

After implementing this if I have some time left I'll also work on the bear creation wizard for the plug-in.
