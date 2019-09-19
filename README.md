# CasperLabs Tech Spec - Sphinx


## Installing Sphinx and Other Modules

Install the following Python packages using pip:

On Mac/Linux:

```
sudo pip3 install sphinx sphinx-rtd-theme recommonmark sphinx-autobuild
```

On Windows:

Start `cmd` in Admin mode. Make sure Python binaries are in your $PATH and run

```
pip3 install sphinx sphinx-rtd-theme recommonmark sphinx-autobuild
```

## Building

Run `make` to see the many output options.

Note: You don't need to be on Linux to work on the TechSpec. You can work on any
OS (e.g. OSX of your choice as long as Python and Sphinx are installed, and relevant
binaries are in your $PATH. Windows doesn't come with `make`, so it might be a
good idea to use
[Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/about).
The other option is to invoke `sphinx-build` directly, e.g.

```
$ sphinx-build -M html "." "_build"
```

### Static HTML

To generate the website, run

```
make html
```

This generates the website under `_build/html/`. To view it, open the file
`_build/html/index.html` in your browser.

### Static HTML - Live

It's too tedious to type in `make html` every time one needs a preview.
[Sphinx Autobuild](https://pypi.org/project/sphinx-autobuild/) is an external
module built to remedy this issue. Files are tracked in real time and the
website is built from scratch every time a change is detected.

To use it, run

```
make livehtml
```

This starts a server which serves the live content on `http://localhost:8000/`.


### PDF through LaTeX

To generate the PDF (LaTeX), run

```
make latexpdf
```

This generates the PDF `_build/latex/CasperLabsTechSpec.pdf`.


**IMPORTANT:** Sometimes the Makefile can't capture all the changes in the
files, and builds fail unless started from scratch. If you run into problems,
run `make clean` before building:

```
make clean; make html
```

or

```
make clean; make latexpdf
```

## Editing

This section outlines a recommended way of editing reStructuredText files.
I chose [VS Code](https://code.visualstudio.com) as an example, but you could
reproduce the same configuration with your own text editor. Editing will not
require a lot of features or IDEs. The only requirement is the 80-character hard
wrap setting. On the other hand, good-to-haves are syntax highlighting,
and keybindings to insert frequently used rst directives such as `:math:\`...\``.


### Setting up VS Code

1. Install VS Code.
2. Install the plugins
[reStructuredText](https://marketplace.visualstudio.com/items?itemName=lextudio.restructuredtext)
and [Rewrap](https://marketplace.visualstudio.com/items?itemName=stkb.rewrap)
3. Go to settings with `Ctrl+,`.
   - Change the setting `Editor: Word Wrap` to `off`.
   - Make sure `Rewrap: Auto Wrap` is `Enabled`.

## Why move away from Gitbook?

We discussed recently how to collaborate on the whitepaper/techspec
It's in gitbook, which changed versions recently:
https://docs.gitbook.com/v2-changes/important-differences
And here are some disconcerting quotes:

> We have moved away from the static site generator model, and no longer use the
> famous gitbook CLI to build documentation output. This has brought a lot of
> benefits and simplicity to the new version, such as instant publishing,
> getting rid of obscure build failures, automatic updates and continuous
> improvement of features for hosted documentations.
>
> We are no longer versioning your books as a Git repository. With the new
> version, we have shifted to a GitBook specific versioning system. Your content
> is still backed-up, versioned, and always available for export, so it is never
> locked on our platform. But we no longer offer this feature in the form of a
> git hosting service.

IMO having a documentation system that supports git is a must. This will be a
specialized technical document which requires features like:
1. LaTeX equations (MathJax must be configurable, apparently one needs to type
   `$$` also for inline equations which @Wojtek and I find stupid)
2. Figures
3. Exporting to both web and PDF
4. other hard to foresee features...

AFAIU gitbook has problems with 1 and 3 already. They removed the CLI build
workflow, which makes it hard to see the output locally. This is a headache when
writing out equations for example. I'm not sure if it's like that now, but
having to commit every time you need to see the output isn't very smart

They removed git, which makes collaboration a headache. *Also, storing document
state in places other than the repo isn't very smart.*
