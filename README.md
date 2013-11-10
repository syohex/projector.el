`projector.el` is a lightweight Emacs library for managing project/repository-aware shell and shell command buffers. A quick overview of features:

* It can spawn both synchronous and asynchronous buffers for shell-commands as well as dedicated `shell-mode` buffers for repositories.

* It uses `ido-mode` for project, buffer, and shell command completion suggestions. Shell command completion candidate suggestions are served from `shell-command-history` in the minibuffer.

* For async processes, it uses [`alert`](https://github.com/jwiegley/alert) for handling the exit message. This makes it easy to hook into notification programs like [`terminal-notifier`](https://github.com/alloy/terminal-notifier) or [`growlnotify`](http://growl.info/downloads).

## Installation

Install it from [MELPA](http://melpa.milkbox.net) or just drop `projector.el` in your load path and add `(require 'projector)` to your initialization.

Set the variable `projector-projects-root` to the root folder for your local projects/repositories:

Optionally, set `alert-default-style` to [one of these](https://github.com/jwiegley/alert/blob/master/alert.el#L123-L128).

example setup:

```
(require 'projector)  
(setq projector-projects-root "~/code/")
(setq alert-default-style 'notifier)
```

## Usage

Then the following functions are available:

* `(projector-run-shell-command-project-root)` - Run the named shell command from the current repository root in a dedicated buffer. With the `C-u` prefix, run the process in the background and output on exit to `terminal-notifier`, `growlnotify`, or Emacs.

* `(projector-run-shell-command-project-root-background)` - Same as running `(projector-run-shell-command-project-root)` with the `C-u` prefix.


* `(projector-run-shell-command-current-directory)` - Run the named shell command from the current directory in a dedicated buffer. With the `C-u` prefix, run the process in the background and output on exit to `terminal-notifier`, `growlnotify`, or Emacs.

* `(projector-run-shell-command-current-directory-background)` - Same as running `(projector-run-shell-command-current-directory)` with the `C-u` prefix.

* `(projector-switch-to-or-create-project-shell)` - Find or create a dedicated shell for the current repository.

* `(projector-open-project-shell)` - Use `ido` to find or create a dedicated shell for a project/repository in your `projector-projects-root`.

* `(projector-switch-to-shell-buffer)` - Use `ido` to switch to any shell buffer opened by `projector`.

* `(projector-switch-to-shell-buffer-in-project)` - Use `ido` to switch to any shell buffer opened by `projector` in the current project/repository.

I will leave the key-binding of these up to you, or you can just call them with `M-x` if you'd prefer.






