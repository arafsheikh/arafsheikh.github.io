---
layout:	post
title: Unix and Windows will never be compatible
date: 2015-06-24 00:13:00
---

After the death of my desktop earlier this week, the only computer I was left with was my dad's laptop. Ditching that old crap wasn't painful. What was painful was moving from Linux to Windows.

The best thing about Linux is you can literally setup almost everything on a new machine in a few minutes. The `home` folder. Copy it, paste it; and you're really home. Alas, the Windows world isn't governed by the same laws.

I had to start from scratch, install stuff like `git`, `vim`, `python`, `ruby`, and configure them. But the pain didn't end there.

After writing my [previous post](/2015/06/23/imagining-is-more-important-than-implementing) I tried to build my website. I opened `command prompt` changed the directory and typed:

`jekyll build`

and everything went fine.

Then I tried to start the server:

`jekyll serve`

and I ended up with:

![](/images/windows-jekyll.png)

After a bit of struggling I found that the default encoding for text file in Windows breaks the Jekyll site. The default encoding is `UTF-8 with BOM`, which is incompatible with Jekyll. Instead it must be `UTF-8`. Furthermore even the line endings were a part of the problem.

Line endings used by Unix are LF (line feed). Windows uses CRLF (carriage return + line feed). Since `Ruby` compiles the site on Windows it expects Windows line endings (obvious but this is where I went wrong).

To set everything right here is what I did:

I used `unix2dos` to recursively convert all files in my site's folder to CRLF line endings. This is the command:

`find ./ -type f -exec unix2dos {} \;`

Enter this command on `Cygwin` or `git bash`, and it should do the trick.