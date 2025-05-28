# Model-View-Controller (MVC)

## Introduction

Divides an interactive application into three elements. The model contains the core functionality and data. Views display information to the user. Controllers handle user input. Views and controllers together comprise the user interface. A change-propagation mechanism ensures consistency between the user interface and the model.

![[Pasted image 20250508144823.png | 300]]

## Model

- provides core functionality
- registers dependent controller and views to notify them of changes

## Controller

- accepts user input as events
- translates events to requests to the model or the view

## View

- creates and inits the associated controller
- displays information
- retrieves data from the model

---

Origin: 
References: 
Tags: 
Created: 08.05.2025

