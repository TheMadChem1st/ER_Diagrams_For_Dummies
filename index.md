# ER Diagrams for Dummies
## A view into the data modeling process

Hello reader! In this tutorial, we are going to cover the process of going from some general-English description of some "miniworld" to an Entity-Relationship, or ER, diagram. Specifically, we are going to guide you along the process of constructing an ER diagram that will represent a K-12 school, and with the concepts that you will learn here you will be equipped to model other systems.

So to begin, let's make sure we are up to speed on the basic building blocks of an ER Diagram!

### Part 1: A quick refresher on ER diagram syntax

#### What is an ER Diagram?
ER Diagrams are a visual representation within a database of how entities relate to each other.
#### Components of an ER diagram
  - Entities
  - Attributes
  - Relationships
  
 ![Components of an ER diagram](https://d3n817fwly711g.cloudfront.net/blog/wp-content/uploads/2012/03/ER-Diagram-Elements.jpeg)
#### Entites
  - Think of entities as nouns - a person or object for example. 
  - Typically shown as a rectangle. 
  - **Entity Types**- A group of definable things such as customers. The entity would then be a single specific customer.   
  - **Entity Set**- A group of definable things defined at a particular point in time. For example, customers who made a purchase in the last month. 
  - **Entity Categories**- There are three categories of entities- strong, weak, and associative. **Strong entities** can be defined solely by their own attributes, while **weak entities** cannot. An **associative entity** associates entities within an entity set. 
#### Relationships 
- Think of relationships as verbs. For example, a carpenter making a table. The two entities would be the carpenter and the table, and the relationship is the act of making, connecting the two entities.  
- Typically shown as diamonds or labels directly on the connecting lines. 

![Image of a Relationship Example](https://d3n817fwly711g.cloudfront.net/blog/wp-content/uploads/2012/03/Relationship-ER-diagrams.jpeg)
#### Attributes 
 - A property or characteristic of an entity. 
 - Typically shown as an oval. 
 - **Multi-value attributes** can have more than one value at a time for one attribute such as multiple hobbies for one person .
 
 ![Image of an attribute](http://jcsites.juniata.edu/faculty/rhodes/dbms/images/eratts.png)
#### Cardinality 
- There are three main cardinal relationships: one-to-one, one-to-many, many-to-many.
- A **one-to-one** example would be a single employee manages one team .
- A **one-to-many** example would be a single customer places many orders . 
- A **many-to-many** example would be many students enrolling for many classes. 

![1-1 Cardinality Image](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/seo/ERD/discovery/erd-chens-13.svg) 
![1-M Cardinality Image](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/seo/ERD/discovery/erd-chens-14.svg)
![M-N Cardinality Image](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/seo/ERD/discovery/erd-chens-16.svg)

### Part 2: The basic elements of our diagram
In this section, we will take those basic blocks from Part 1 and put those to use in figuring out how to select the appropriate **entities** and **attributes** from the general description of a K-12 school. We can refer to this school, which can be thought of as a slice or subset of the real world, as a **miniworld**. Other examples of a miniworld could be a hospital, a city, or a business. 

#### The Miniworld Description
This school is mainly comprised of students, teachers, staff, and classes. 

Each student has:

* One or more classes they are enrolled in, with a current grade for each class
* A name
* An unique student ID number
* An age

Each teacher has:

* A name
* A unique teacher ID number
* One or more classes that they teach
* An age

Each staff member has:

* A job title
* An unique staff ID number
* A name

Each class has:

* One or more enrolled students
* One or more teachers
* A course-specific ID number
* A 3 or 4 letter subject code
* A 3-digit class number 
* An unique class ID code

#### Where to start?
##### Problem 1

So, a great place to start here is in selecting our initial **entity** types. In other words, what kinds of *components* make up this world? In the following list, please select what you think are the essential basic types of things in this world. 

* Students 
* Grades
* Names
* Teachers
* Classes
* Nachos
* Staff members
* The School Principal
* Senior Pranks

##### With your selections in hand, please compare to our answers at the end of this tutorial before reading on. 

 ----------------------------

Yep, just four! For the sake of brevity, we are keeping this miniworld pretty simple. As Bob Ross might say, "only fill your world with the details we want to be in it."
 
 So, why did we only pick these options instead of something like "Grades"? Well, in this example a grade does not really exist as a standalone item as a grade needs to be connected logically to something like a class or an assignment to make sense. At this stage we are only concerned with the fundamental components that make up this Miniworld, and it does not make much sense for a school to have some detached "Grade" property associated with it. 

#### Putting things in boxes
So, we now have our four main building blocks that make up the essential components of this K-12 school. Thinking all the way back to Part 1, what syntactical element of an ER diagram would we use to represent these **entitites**?

##### Problem 2

* A rectangle
* A circle
* A box inside of a box
* A circle inside of a circle
* A 32-sided 3D polygon
* A cute drawing of a giraffe playing with a panda outside of a school

##### With your selection in hand, please compare to our answers at the end of this tutorial before reading on. 

-----------------------------

#### What about their stuff?
So as indicated by the Miniworld description, these basic **entities** have various associated **attributes** that help define them. A basic example of this is that each student has a name, an age, and some other details. Each teacher has a job title, a staff ID number, a name, and some number of classes that they teach. So, how do we diagram these **attributes** to show their association to their respective **entities**?

Recall from Part 1 that attributes are represented by putting the attribute name inside of a single circle. We have two special cases to consider here: **key attributes** and **multi-valued attributes**.

##### Key attributes
A **key attribute** is an attribute or set of attributes that are *guaranteed to be unique* for any particular entity. For example, a name of a student or a teacher would not be expected to be unique. However, something like a unique ID number would be valid for consideration as a key attribute. **Key attributes** are denoted by an underline.

##### Multi-valued attributes
A **multi-valued attribute** is some attribute where it will have multiple values rather than just one. Hypothetically, if we had a new attribute for each student that would contain a list of foods that the student is allergic to (such as peanuts, bananas, salad), that would constitute a multi-valued attribute. For our situation here, an example of a multi-valued attribute would be that each teacher has one or more classes that they teach. 

So, we will save the longer task of drawing all of these attributes for the next part, but please take a moment to look through the miniworld description and for each attribute, identify whether it is a basic attribute, a key attribute, or a multi-valued attribute. 

Once that is complete, we are ready for Part 3!



### Part 3: Getting serious with relationships

In this section we will take the entities from Part 2, and establish relationships between those entities to define how they interact.

#### Where to start

We can begin building relationships by considering how the entities interact in real life.
#### Problem 3.
Consider the following possible relationships:

* Students and Teachers
* Teachers and Classes
* Teachers and Staff
* Classes and Students
* Classes and Staff
* Staff and Students

Which of these relationships should be defined? What sort of relationships are they? Compare your answers to the ones at the bottom of this tutorial.


#### Why these relationships?

Why should we use these relationships, and not the others I mentioned? Because these ones enable us to link all the entities together in a way that makes sense, and has relatively few links. Technically we could of established a relationship between Teacher and Student, but would that really add anything to our diagram? We don't really need to establish a connection between Teacher and Student, because they are already both related to Class

### Part 4: Connecting the dots

Ok so now we are close to the end! Lets start out with this almost finished ER Diagram and then identify what can be changed. 
![Basic ER DIAGRAM IMAGE](https://i.gyazo.com/61fb40872517e95a1bb598bb623caa62.png)

Now with this ER Diagram, We can see everything we have learned so far put together with the basic entity types, relationships connecting them, and the attributes of each entity. 
One thing we can do to make it better is to take this ER diagram and make sure the relationships match our cardinality requirements. I left that out so you can put it in yourself and then you can check below to make sure you got it correct.




### Problem Solutions

#### Problem 1:

* Students
* Teachers
* Staff members
* Classes

---------------------------------

#### Problem 2:

An **entity** is represented by a rectangle.

---------------------------------

#### Problem 3:

* Students and Classes are linked by the Enrolled_In relationship
* Classes and Teachers are linked by the Teaches relationship
* Teachers and Staff are linked by the Member_Of relationship

## ER DIAGRAM WITH CARDINALITY

![ ER DIAGRAM IMAGE](https://i.gyazo.com/a6709375de95e25dd6deec1f6c476fc9.png)
