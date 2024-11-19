# On Package Management
Managing dependencies when programming is tricky, and Python doesn't make it fun. Python standardizes Pip and the way it works, but it's not terribly complex and doesn't handle more advanced concepts like Virtual Environments. It can also break packages (system installed or otherwise) very easily, and despite being usable in most cases, further extension is necessary. I have decided that an extended package manager is needed to effectively work with Python and FRC code, and so I write this to expand on what and how to use the abstractions defined in our standards.

## Pipenv vs Pip
I decided, after a little searching, that Pipenv complied with the warrants that an FRC and RobotPy project needs. In terms of functionality, Pipenv has a few things that, in my opinion, make it a little more usable for this purpose. Pipenv, among other things, uses a standard configuration to define packages and configuration for build and deploy scripts. It also automatically handles the creation and management of Virtual Environments, which prevents Robot Code and dependencies from interfering with anything else installed on any given computer. See below figure 1 and figure 2 which show the pros and cons of Pip, briefly summarized. There are many more nuances that are necessary to understand, but those are outlined in [programming/pipenv](/docs/programming/pipenv)

### Pipenv (Figure 1)
| Pros      | Cons |
| ----------- | ----------- |
| Virtual Environments      | Much more complex than Pip      |
| Scripts in Configuration   | More documentation work necessary (nonstandard)        |


### Pip (Figure 2)
| Pros      | Cons |
| ----------- | ----------- |
| Simple and easy to use      | Can easily break system       |
| HIGHLY documented and used in RobotPy/WPI docs   | Lacks certain configuration features        |

## Why not Poetry, PDM, etc?
I chose Pipenv on a whim, honestly. But after reading about some features of Pipenv when compared with Poetry and some others, I found that it would have an easy enough learning curve and has sufficient features when compared with it's contemporaries in other languages (see NPM, Cargo, etc)

zach is making me write this - kay