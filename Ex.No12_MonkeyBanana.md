# Ex.No: 11  Planning –  Monkey Banana Problem
### DATE: 30.03.2024                                                                          
### REGISTER NUMBER : 212221040157
### AIM: 
To find the sequence of plan for Monkey Banana problem using PDDL Editor.
###  Algorithm:
Step 1:  Start the program <br> 
Step 2 : Create a domain for Monkey Banana Problem. <br> 
Step 3:  Create a domain by specifying predicates. <br> 
Step 4: Specify the actions GOTO, CLIMB, PUSH-BOX, GET-KNIFE, GRAB-BANANAS in Monkey Banana problem.<br>  
Step 5:   Define a problem for Monkey Banana problem.<br> 
Step 6:  Obtain the plan for given problem.<br> 
Step 7: Stop the program.<br> 
### Program:

### MONKEY BANANA DOMAIN

```
(define (domain monkey)	       
  (:requirements :strips)
   (:constants monkey box knife bananas glass waterfountain)
   (:predicates (location ?x)
	       (on-floor)
	       (at ?m ?x)
	       (hasknife)
	       (onbox ?x)
	       (hasbananas)
	       (hasglass)
	       (haswater))
   ;; movement and climbing
  (:action GO-TO
	     :parameters (?x ?y)
	     :precondition (and (location ?x) (location ?y) (on-floor) (at monkey ?y))
	     :effect (and (at monkey ?x) (not (at monkey ?y))))
   (:action CLIMB
	     :parameters (?x)
	     :precondition (and (location ?x) (at box ?x) (at monkey ?x))
	     :effect (and (onbox ?x) (not (on-floor))))
   (:action PUSH-BOX
	     :parameters (?x ?y)
	     :precondition (and (location ?x) (location ?y) (at box ?y) (at monkey ?y) 
				 (on-floor))
	     :effect (and (at monkey ?x) (not (at monkey ?y))
			   (at box ?x)    (not (at box ?y))))
  ;; getting bananas
  (:action GET-KNIFE
	     :parameters (?y)
	     :precondition (and (location ?y) (at knife ?y) (at monkey ?y))
	     :effect (and (hasknife) (not (at knife ?y))))
  (:action GRAB-BANANAS
	     :parameters (?y)
	     :precondition (and (location ?y) (hasknife) 
                                 (at bananas ?y) (onbox ?y))
	     :effect (hasbananas))
  ;; getting water
  (:action PICKGLASS
	     :parameters (?y)
	     :precondition (and (location ?y) (at glass ?y) (at monkey ?y))
	     :effect (and (hasglass) (not (at glass ?y))))
  (:action GETWATER
	     :parameters (?y)
	     :precondition (and (location ?y) (hasglass)
				 (at waterfountain ?y)
				 (at monkey ?y)
				 (onbox ?y))
	     :effect (haswater)))
```

### Input 

### PROBLEM 1

```
(define (problem pb1)
    	(:domain monkey)
  	(:objects p1 p2 p3 p4 bananas monkey box knife)
  	(:init (location p1)
		(location p2)
		(location p3)
		(location p4)
	 	(at monkey p1)
		(on-floor)
		(at box p2)
		(at bananas p3)
	 	(at knife p4)
	)
  	(:goal (and (hasbananas)))
)
```

### Output/Plan:

OUTPUT 1

<img width="359" alt="s1" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/0aa0e0ca-a3b0-4544-8224-e4963e2549d1">

OUTPUT 2

<img width="348" alt="s2" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/2e365c0a-4a4a-4167-8a4a-b40bebb975aa">

OUTPUT 3

<img width="338" alt="s3" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/db699417-7172-4833-b70a-d4ea4c411827">

OUTPUT 4

<img width="365" alt="s4" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/823eae46-84db-4b51-a004-03cd875300f8">

OUTPUT 5

<img width="344" alt="s5" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/4a9d1de0-d219-4332-ba73-63d86518d5c8">

OUTPUT 6

<img width="346" alt="s6" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/93d3ac05-4a50-4722-9a6a-c1c1ee9cf14b">


### Result:
Thus the plan was found for the initial and goal state of given problem.
