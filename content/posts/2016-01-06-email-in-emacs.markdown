---
categories: null
comments: true
date: 2016-01-06T22:22:50Z
excerpt: null
image:
  feature: null
modified: null
tags:
- emacs
title: Email in Emacs
---

So as part of my plans for the new year is consolidating my tools. The first thing that I've done is start to use Emacs and [Mu4e](http://www.djcbsoftware.nl/code/mu/mu4e.html) to handle all my email.

The first thing I set up is [Offlineimap](http://offlineimap.org/). This pulls mail down from all three of my accounts ( personal, domain, and work ) into maildirs that [Mu](https://github.com/djcb/mu) can index.

Here's what the config looks like for a single account:

{{< highlight yaml >}}
[general]
accounts = Gmail, Bardel, SeanHagen
maxsyncaccounts = 1
pythonfile = ~/.offlineimap.py
fsync = False

[Account Gmail]
localrepository = LocalGmail
remoterepository = RemoteGmail
status_backend = sqlite

[Repository LocalGmail]
type = Maildir
localfolders = ~/Mail/Gmail

[Repository RemoteGmail]
type = Gmail
remoteusereval = get_username("mail.google.com")
remotepasseval = get_password("mail.google.com")
realdelete = no
maxconnections = 3
sslcacertfile = /etc/ssl/certs/ca-certificates.crt
folderfilter = lambda folder: folder in ['[Gmail]/All Mail', '[Gmail]/Sent Mail', '[Gmail]/Drafts', '[Gmail]/Trash', '[Gmail]/Starred']
nametrans = lambda foldername: foldername.replace("[Gmail]/","")
{{< / highlight >}}

There's just a few things here to point out. The _pythonfile_ setting lets you provide a Python file to define methods to use in the configuration. This Python file in particular is one I found online somewhere, and I've put up [in a Gist](https://gist.github.com/5e9d0d9ce55b6415beb3) so you can use it too. Anyways, this one grabs the username and password from my Gnome Keyring -- which is nice, because then it doesn't live in plain-text in a config somewhere.

To store the password, I use a separate script that I also found online ( [and also put in a Gist](https://gist.github.com/4cec710ca75e86eaad8c) ) to store usernames and passwords in the keyring.

To send email, I've got a Postfix configuration that lets me specify "localhost" as the SMTP server, and then Postfix handles actually sending them. I like this setup for a few reasons. The first is that Emacs doesn't hang while trying to connect and send the email. The second is that if I'm on my laptop and not connected to the internet Postfix will handle queuing up the email to send later when it's connected to the internet again.

Lastly, there's my Mu4e configuration. Below is the compressed version ( and the [Gist is up here](https://gist.github.com/e5e24dd2e9dd575f68ef) ):

{{< highlight lisp >}}
;; mu4e stuff
(require 'mu4e)

;; tell message-mode how to send mail
(setq message-send-mail-function 'smtpmail-send-it)
;; if our mail server lives at smtp.example.org; if you have a local
;; mail-server, simply use 'localhost' here.
(setq smtpmail-smtp-server "localhost")

(setq mu4e-view-prefer-html t)
(setq mu4e-view-show-images t)
(setq mu4e-view-show-addresses t)
(setq mu4e-headers-skip-duplicates t)
(setq mu4e-use-fancy-chars nil)

(add-to-list 'mu4e-view-actions
             '("in browser" . mu4e-action-view-in-browser) t)


(add-hook 'mu4e-compose-mode-hook 'flyspell-mode)
;; gpg
(add-hook 'mu4e-compose-mode-hook 'epa-mail-mode)
(add-hook 'mu4e-view-mode-hook 'epa-mail-mode)

;; set this to nil so signature is not included by default
;; you can include in message with C-c C-w
(setq mu4e-compose-signature-auto-include ‘t)
(setq mu4e-compose-signature (with-temp-buffer
                               (insert-file-contents "~/.signature.personal")
                               (buffer-string)))

;; message-signature-file NOT used by mu4e
(setq message-signature-file "~/.signature.personal")

;; use imagemagick, if available
(when (fboundp 'imagemagick-register-types)
  (imagemagick-register-types))

(defun my-render-html-message ()
  (let ((dom (libxml-parse-html-region (point-min) (point-max))))
    (erase-buffer)
    (shr-insert-document dom)
    (goto-char (point-min))))
(setq mu4e-html2text-command 'my-render-html-message)

(defvar mu4e-bookmarks
  '(("date:1d..now flag:unread AND NOT flag:trashed" "Unread from last 24h messages"      ?r)
    ("flag:unread AND NOT flag:trashed" "Unread messages"      ?u)
    ("date:today..now"                  "Today's messages"     ?t)
    ("date:7d..now"                     "Last 7 days"          ?w)
    ("mime:image/*"                     "Messages with images" ?p))
  "A list of pre-defined queries; these show up in the main
screen. Each of the list elements is a three-element list of the
form (QUERY DESCRIPTION KEY), where QUERY is a string with a mu
query, DESCRIPTION is a short description of the query (this
shows up in the UI), and KEY is a shortcut key for the query.")
{{< / highlight >}}

There's still a few things I've got to figure out.

I'd like to figure out a better way to view HTML email. Right now, I'm using the built-in Emacs HTML renderer ( part of eww ). If the email doesn't come out well, the following bit of code adds another action:

{{< highlight lisp >}}
(add-to-list 'mu4e-view-actions
             '("in browser" . mu4e-action-view-in-browser) t)
{{< / highlight >}}

What that does is let me open the HTML version of the email in a browser by pressing 'a', then 'i' when viewing an email.

I've also got to figure out an easy way to search through Mu's email addresses so I can have some sort of address book, although the auto-complete seems to work pretty well so far.

There will probably be a few other things that come up over the next few months, but I'll handle them when they come up.
