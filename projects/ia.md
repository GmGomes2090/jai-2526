# Project 1 - Individual Assignment

## Objectives

- Create a 3D platform game using Unity
- Do the assignment by yourself
- Learn and expand your knowledge in Unity programming using the course’s concepts

## Description

You are required to program a platform 3D (**mandatory**) video game consisting of a single level (~3 minutes of play). There is only one player and its abilities are the traditional walking/running movements, as well as jumping. The level should present challenges that need to be solved to win.

You can opt for first/third person with camera attached to the player, or a sideways view with the camera keeping the player framed (continuos or discrete scrolling is possible)

The player will face dynamic opponents and static hazards, as well as obstacles. Some type of injury or damage is inflicted to the player when running into opponents. Don’t forget to define the winning and losing conditions. Some of the platforms should be dynamic. The player can collect items and power ups (that change its abilities). A minimal GUI will provide information about these items, power ups and energy/life points.

## Game checklist and evaluation guide

The evaluation is decomposed into:
- Title, minimal story, winning conditions (2 points) - written in the video or in the game
- static platforms, moving platforms, collectables and power-ups (4 points),
- State Variables (Ex: life, ammo), minimal GUI (2 point),
- mobile enemies that can throw things at you (use jump or duck to avoid), obstacles (things that merely block your path) and hazards (health/life) (6 points),
- Character animation or complex animator (min: standing, walk, jump) (2 points)
- Peer to peer video evaluation - Technical and Visual and Audio Achievement (4 points)
- Program shortcut keys (1,2,3,4…) to facilitate the final discussion of the assignment by jumping to predefined locations and states.
Full score is given if you illustrate each point significantly (more than once).

## Delivery (March 29, 23h59)

There are two major deliverables:

- A repository with the source code of your project. Please accept the invitation here: [https://classroom.github.com/a/elKuwZY2](https://classroom.github.com/a/elKuwZY2). Rename your repository to be in the form: **ia_NNNNN_FirstName_LastName**, where NNNNN is your student ID.
- A video of up to 1 minute covering all the requirements shared with a google drive link (shared with “anyone with a link”).

For the actual submission you will need to provide a Game Title, the repository url, a list of external addons and assets used and the video url.

Please use this google form and login using your @campus.fct.unl.pt account:

Submission form: DUE DATE EXCEEDED<!--[https://forms.gle/A5QdFrFBLpsQSpwC7](https://forms.gle/A5QdFrFBLpsQSpwC7).-->

## How to connect your empty Unity Project to your repository

First, create a new Unity Project using the template "Core Universal 3D" in some location of your choice.

Now do this:

- Launch a terminal window
- Change directory to the Unity Project location you just created
- type the following commands:
    - `$ git init .`
    - `$ git remote add origin <your_assignment_repository_url>`
    - `$ git pull origin main`
    - `$ git add .`
    - `$ git commit -m "Added Initial Unity project."`
    - `$ git git push --set-upstream origin main`

Have fun!