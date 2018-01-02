# A new way to manage Emacs

I have been managing my Emacs config with packages for a few
years. But I am finding 3 problems with it:

1. there is quite a lot of overhead in managing packages
2. I am sick of the complexity involved in moving my emacs around machines
3. I am worried about the security of packages that get updated and I don't review the updates

This repository is my way of dealing with these problems.

## Solving the problems

I don't aim to solve problem #1 particularly. There will always be overhead.

But problem #2 and #3 seem related. 

I think the answer to packaging systems is really what golang has
done. Source code repository based packaging. In brief this has the
following properties:

* one namespace is used for all packages, there is no per-project package namespace 
* packages are version controlled source repositories

This has the following advantages:

* it homogenizes into the VCS all the version control requirements
 * need two different versions of the same library for two different projects? they should be represented as two different branches in the same "package"
 * want to make a change to a package to faciltate something in a dependency? just change the source code and recompile
* security can be handled by using VCS commits
 * you can approve the state of a project at a particular version and be confident that won't change
 * you can potentially share your trust of a particular commit
 
This approach does not work well with Java, or other partially
compiled lanaguages. But for both native compilation and dynamically
compiled languages (like Python or EmacsLisp) it works well.

