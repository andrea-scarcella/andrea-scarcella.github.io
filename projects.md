---
layout: default
title: Projects
---
#Welcome to my project page!

Here you can find a list of my projects

## Window state management component

### Requirements
Design a state management component for a multi-window application.

Each window provides an interface to browse entities and perform operations on them.

The window state determines the operation to be performed, for instance in the 'Add' state the current entity is persisted.

### Design choices
State transitions are modelled as user-defined events.

### Diagram Key
Each node represents a window state

Each edge label represents a user action

'Closed' is an absorbing state

### State machine diagram
![State machine example] (https://rawgithub.com/andrea-scarcella/assorted-work/master/DesignDocuments/simpleWindowStateMachine.svg)

   