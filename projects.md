---
layout: default
title: Projects
---
#Welcome to my project page!

Here you can find a list of my projects

## Window state management component

### Requirements
Design a state management component for a multi-window application.

Each window provides an interface to browse business objects and perform operations on them.

The window state determines the operation to be performed, for instance in the ‘Add’ state the current entity is persisted.

### Design choices
The architecture used in this project is MVC.

The underlying idea is to abstract the windows behaviour in terms of states from its concrete implementation, this is achieved as follows:

1. a state machine (see diagram) models the high-level window behaviour and exposes events that are fired on a state transition.
2. the window class has a dependency on the interface implemented by concrete state machines. It does not manipulate its dependency directly but provides it to a third party (a window controller, see below) that will in turn use it.
3. a window controller translates window widget events into state machine transitions and handles events raised by a state machine by modifying the state of the widgets of a specific window instance.

A concrete example of how this solution works is the following

1. a new instance of a window is created, a new instance of a state machine is passed as a dependency
2. the browse button of a window instance is clicked (e.g. ‘browseButtonClicked’)
3. the corresponding event is handled by the corresponding window controller method
4. this method retrieves the state machine instance from the window instance that raised the event and calls the corresponding transition.
5. depending on its state, the state machine instance raises a specific event
6. this event is in turn handled by the window controller that implements at a lower level of abstraction by manipulating window widgets directly.

A distinct advantage of this approach is the loose coupling between the components (design by contract + dependency injection) and the separation of responsibilities (state machine defines high-level behaviour, controller translates low-level widget events into state machine behaviour and implements it by manipulating widgets, view generates low-level events and holds a reference to its state) .

### Diagram Key
Each node represents a window state

Each edge label represents a state machine action

The semantic of each state is defined as follows:

Add state: new record data can be supplied

Ok state: current (unedited) record data is displayed

Update state: current record data has been modified

warn states: a warning has been issued to the user, it can either be dismissed therefore completing the action or it can be confirmed thus cancelling the requested action.

The state machine diagram can be found in the corrisponding section.

### State machine diagram
![State machine example] (https://raw.github.com/andrea-scarcella/assorted-work/master/DesignDocuments/windowStateMachine.png)

   