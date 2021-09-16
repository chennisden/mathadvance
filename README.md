# Math Advance Contributor Guidelines

Are you a new or prospective contributor to Math Advance? Then this is the right place for you! Enclosed here are some contributor tips and guidelines.

Depending on how many permissions you have within Math Advance, you may not be able to see some of the repositories I am mentioning. If you can't see a repository you are interested in, email me at [dchen@mathadvance.org](mailto:dchen@mathadvance.org) and request for access.

## Committing and Pushing

If you have direct commit/push access, **commit to dev branches**. Don't commit to the main branch for anything other than "version releases". If you don't, fork and pull request once you're done. You should pull request to main since it's actually stable.

## Technology Guidelines

If you have access to the MAST repository, please make sure you compile PDFs correctly. Typically this requires a working `latexmk` setup with a `.latexmkrc` that compiles Asymptote. **If you send in a commit that doesn't have a PDF compile I will reject it. If you send in a commit that has a PDF compile without diagrams I will reject it.**

As a rule of thumb, I do not want edits from people using Overleaf or people improperly using Git. This is because these traits are correlated with writing incredibly ugly LaTeX that I have to clean up later (or straight up incorrect LaTeX), and it's just not worth the effort. In theory, if you wrote really clean LaTeX and good commit messages, I wouldn't be able to tell the difference, but in practice it's night and day.

If I reject changes it's because they're bad, but the root cause is almost always using technology incorrectly. So I strongly recommend you take the time to get a working LaTeX and Git installation. It literally involves typing
    
    sudo apt install git
    sudo apt install texlive

(or the equivalent) so it really is not that hard to get started.

## LaTeX

Most LaTeX projects require certain custom packages or classes. A quick summary of repositories you may need to reference:
    
- [chennistex](chennisden/chennistex):
    Contains `lucky.cls`, among other things you do not have to care about.

- [bounce](chennisden/bounce): Contains `bounce.cls` (no surprise). I don't think mathadvance projects ever use it, but I'm listing it just in case.

- [macontest](chennisden/macontest): The Math Advance contest class. It's internal and pretty much only used for MAT.

- [mabook](chennisden/mabook): The Math Advance book class. It's internal because I don't want other people compiling books with our look. But if you intend on writing a book for Math Advance, pitch the idea to me and I'll give you access to the class.
    - [scrambledenvs](chennisden/scrambledenvs): Creates scrambled hints and solutions for books. Typically used in *my* books, but other authors may choose to do otherwise.

        Note that the install instructions are different. They are listed in the `scrambledenvs` repository.

Here are the classes you will need to install for the following mathadvance projects:

- `mast`: get `lucky.cls` from `chennistex` (I don't care if you clone the entire repository or just download `lucky.cls`, but I recommend the former.)
- `mac-contests`: get `macontest.cls`
- `geo-foray-textbook`: get `mabook.cls` and `scrambledenvs.sty`

### Install Instructions

You should learn about the TEXMF trees if you don't know about them already. It is typically recommended to install custom classes and packages in the `TEXMFHOME` directory, which is located at `~/texmf`.

Go to the directory `~/texmf/tex/latex` (create it if it does not already exist) and clone the GitHub repositories in that directory. That's it.

## Web

There are three main ways you can contribute to the website:

1. Content
2. Visuals (frontend)
3. Website Logic (backend, mostly, but also some Next JS rendering shenanigans)

To propose a change, fork the repository, commit your changes to the fork, and send in a pull request to the master/main branch.

Don't worry about messing things up if you're a beginner. You literally do not have the ability to mess things up besides your own fork because you don't have write access to any of the repositories. Experiment, see what you can learn, and send in a pull request once you have something you're happy with.

### Content

`mast-web` pages are written in MarkdownX. It's like Markdown, but you can also import JavaScript components. In practice you will mostly be writing Markdown and not a lot of X.

Markdown is super easy to learn by example, so I will not elaborate there. Just look at the source of this file!

### Visuals

We use Tailwind CSS in pretty much all of our projects.

### Logic

We use Next JS for all of our projects and slug through `pages` for `.mdx` (MarkdownX) files. As for backend, `mast-web` uses MongoDB with Next JS. We are using Vultr to host our servers.
