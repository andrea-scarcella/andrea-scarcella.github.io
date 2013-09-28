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
The architecture used in this project is MVC.

Every window object has a constructor dependency on an instance of the right state machine.

When the window object raises specific events, such as 'browse', the appropriate controller method is invoked e.g. controller.onBrowse(win,evt)

This method retrieves the state machine of the window that generated the event, and invokes its corresponding transition e.g. 'browse'.

The state machine instance raises the corresponding event e.g. 'browseEvent', passing the window instance as a parameter.

That event is intercepted by the controller and handled accordingly, i.e. the state of a subset of the window widgets is modified to reflect the state transition.

A distinct advantage of this approach is the loose coupling between the components (design by contract + dependency injection) and the separation of responsibilities (state machine defines high-level behaviour, controller implements it, view generates low-level events) .


### Diagram Key
Each node represents a window state

Each edge label represents a user action

'Closed' is an absorbing state

### State machine diagram
![State machine example] (https://rawgithub.com/andrea-scarcella/assorted-work/master/DesignDocuments/simpleWindowStateMachine.svg)

   