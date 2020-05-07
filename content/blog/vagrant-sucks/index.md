---
title: Vagrant Is Bad and I Hate it
date: "2020-03-14T14:01:11.329Z"
description: The pitfalls of Vagrant development on Windows.
---

Working on a virtual machine has many benefits for web developers. It gives access to linux for Windows and Mac users but more importantly it allows for reliable and standardized porting for tailored distributions.

Vagrant is a solution that satisfies these requirements but in the end has some major shortcomings that make it very inconvenient to use on windows.

---

1. 
One of the issues that I ran into time and again was the fact that Windows does not support symbolic links, even though they are expected to be standard on the operating system I was developing with.

Notably this reared it's head while installing many node packages with `npm`. It took many headaches to find the underlying cause of this error and I was actually able to find a work around. 

When using `npm` I could use the flag `--no-bin-links` which would allow the package to be installed at the very least.

--- 

2. 
An unavoidable consequence of symbolic links was the inability to use `create-react-app` for one of my in class projects.

The installation process had unavoidable code that used symbolic links upon initialization so I had to switch to Windows development to even initialize the repository.

This was another large time synch of days trying to make things work with Vagrant. In the end it took 15 minutes to change over to Windows and get my project running without error.

---

3. 
Another hurdle to development was sorting out port forwarding for non-standard servers like some node apps. 

This was an absolute headache to get the correct port forwarding to work and in the end I ended up abandoning Vagrant to work on Windows and a clean Google Cloud instance.

---

All in all Vagrant is a great tool that can be used very effectively under the right circumstances. 

But when it comes to some minutia it is very frustrating to work with a machine that is faking its own identity and lying to the programs its running. 

I would highly recommend against JavaScript development on Vagrant.