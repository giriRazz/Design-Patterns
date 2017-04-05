# Binding properties

### In software engineering, a software design pattern is a general reusable solution to a commonly occurring problem within a given context in software design. It is not a finished design that can be transformed directly into source or machine code.

### The Binding properties pattern is combining multiple observers to force properties in different objects to be synchronized or coordinated in some way. This pattern was first described as a technique by Victor Porton.This pattern comes under concurrency patterns.

## Implementation

## There are two types of binding. One-way binding should be applied when one of the properties is read-only. In other cases, two-way binding must be applied.

##  Problem:
###    We often need to keep synchronized properties of several objects. One place where it is repeatedly encountered is GUI programming: we may need to keep synchronized a check box and a menu item, a control and UserPreferences object, model and view in ModelViewController etc. It is also encountered in DiscreteModelling, electronics, etc.
 ## The problem can be formally expressed as a set of EqualityConstraints.
 ### Attempts to solve this problem naively very often result in infinite loops and other errors which sometimes are hard to debug.
 ## Solution :
 ### Infinite loops can be eliminated by blocking the signal, or comparing the assigned value with the property value before assignment, or eliminating unnecessary assignments.

## Binding Properties with a Transformation: 

### Binding properties with transformations can be achieved through reducing the transformation function to the problem of binding properties, and the function can be imaginary consider as Type Conversions.



         
   ![binding_properties_pattern](https://cloud.githubusercontent.com/assets/26067522/24689864/5190391e-197e-11e7-88f2-     d84def76393e.png)




### A common case of binding properties with a transformation is binding boolean properties with mutual negation.
## Binding Multiple Properties'
### Resulting context:
### Properties are kept synchronized completely automatically. Between library calls they always have the values expressed by the EqualityConstraints.

## Deficiencies:
### Watching over property changes requires some resources. These resources may be sometimes unnecessarily wasted on properties changes of which no one observes for.

## Sample code

### Code sketch for one-way binding may look like as follows:

### bind_multiple_one_way(src_obj, src_prop, dst_objs[], dst_props[])
### {
### for (i, j) in (dst_objs, dst_props)
###  {
###   bind_properties_one_way(src_obj, src_prop, i, j);
###  }
### }

## Two-way binding is simply expressed in terms of one-way binding:

###  // In this pseudo-code are not taken into the account initial values assignments
###  bind_two_way(prop1, prop2)
###  {
###    bind(prop1, prop2);
###    bind(prop2, prop1);
### }


## Binding is accomplished by connecting the property change notification in the following event handler:

### on_property_change(src_prop, dst_prop)
###  {
###    block_signal(src_obj, on_property_change);
###    dst_prop := src_prop;
###    unblock_signal(src_obj, on_property_change);
## }
 
 
 


