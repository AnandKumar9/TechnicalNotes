https://www.juniordeveloperdiaries.com/emacs-intro/
https://www.youtube.com/watch?v=vtmlA5yFvYI&t=222s
https://www.gnu.org/software/emacs/tour/
https://www.masteringemacs.org/article/beginners-guide-to-emacs

 Set a keybinding, write a custom function, create a new tool, of look for an existing tool.

emacs is a lisp interpreter with some added functionality for editing text. Dotfiles that are loaded when emacs starts.

`Frame` - one running instance of an emacs client. Each frame holds at least one *window*
`Buffer` -  holds the contents of files that are being visited
`Window` - area of screen that displays a buffer

`C` - Control key
`M` - Option key

By default, Terminal does not have the Meta key activated. it needs to be activated from the Preferences ('Use Option as Meta key').
![[13. Tools/1. Text Editors/2. Emacs/assets/Misc.png]]

Copying and pasting - Killing (C-w) and yanking (C-y)

'Mini buffer' at bottom.
C-x and C-f - Find file (a function for finding files in current directory)
`emacs-lisp-mode` - Gets emacs to a mode where it things its work with emacs-lsip (elisp) source files.

Emacs packages are written in elisp and are hosted on various package repositories such as Milky Postmans E-Lisp Package Archive

`C-x C-c` - Exit emacs
`C-x b` - New buffer

`C-h C-h` - List of all Help options
`C-h t` - Tutorial
`C-h r` - Manual