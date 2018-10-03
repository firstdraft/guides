# Using Git to freely experiment and never lose work

## What Git is

[Git](https://en.wikipedia.org/wiki/Git) is an extremely powerful **version-control system** created by Linus Torvalds in 2005 for development of the Linux kernel, which is one of the largest open-source software projects in existence. It makes it possible for large numbers of contributors to work on various features, all within a single codebase (which could be comprised of hundreds or thousands of files).

Bitbucket, GitLab, and especially GitHub (all private companies) rode the rise of Git (the protocol) to become the center of the software development universe. All of these companies basically offer cloud-based storage for codebases using Git  for version-control (we refer to these codebases as **repositories**), as well as a web-based interface for collaborating on them — following, commenting, etc.

## Why we care

In this course, we're going to use one simple but effective Git-based workflow to save versions of our work. This will allow us to freely experiment with different approaches, while never having to throw away code.

In all of our Rails apps, after you start the server, you can navigate to the address `/git` in your browser and it will open a page that looks like this:

![](/assets/git-clean.png)

As soon as you make any changes to any of the code in the project, and refresh this page, the lines that you changed will appear:

![](/assets/git-changes.png)

On the left, you see the code as it was previously; on the right, you see the new code. Lines added are highlighted in green, lines removed are highlighted in red.

Below, there are two things you can do: **commit** your changes on the left, and switch to a new **branch** on the right. When you hear the word "commit", think "snapshot". When you hear the word "branch", think "version".

A Git commit is a snapshot of _all_ of the folders and files in your project _at a particular time_. Since our files of code are all interdependent, it doesn't make sense to save versions of individual files — we need to know the _entire_ state of the project for a version to be useful.

The most important thing for you to remember is simple: **commit early and commit often**. As long as you are taking snapshots of your work at various points, it will always be easy to get back to a previous version in case you want to start over and explore a different approach.

To commit, enter a title for the snapshot (required), and, optionally, a longer description:

![](/assets/git-commit.png)

After you commit, you will no longer have any pending changes:

![](/assets/git-changes-committed.png)

If you edit your code again, then you can make further commits.

## For now, that's all you need to worry about. Just make lots of commits as you work.

The best time to commit is after you just got something to work, before you start on your next experiment.

In the History dialog at the bottom, you can see a list of all of the commits you've made. If you want to jump back in time to one of them, copy the 6 letter code in front of it into the field above and then pick a name for a new version. It will snap all of the files in the project back to that point in time, and you can now make further commits along a new path — while still retaining all of your old commits on the old path.