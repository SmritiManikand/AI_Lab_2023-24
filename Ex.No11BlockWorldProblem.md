# Ex.No: 11  Planning –  Block World Problem 
### DATE: 30.03.2024                                                                           
### REGISTER NUMBER : 212221040157
### AIM: 
To find the sequence of plan for Block word problem using PDDL  
###  Algorithm:
Step 1 :  Start the program <br>
Step 2 : Create a domain for Block world Problem <br>
Step 3 :  Create a domain by specifying predicates clear, on table, on, arm-empty, holding. <br>
Step 4 : Specify the actions pickup, putdown, stack and un-stack in Block world problem <br>
Step 5 :  In pickup action, Robot arm pick the block on table. Precondition is Block is on table and no other block on specified block and arm-hand empty.<br>
Step 6:  In putdown action, Robot arm place the block on table. Precondition is robot-arm holding the block.<br>
Step 7 : In un-stack action, Robot arm pick the block on some block. Precondition is Block is on another block and no other block on specified block and arm-hand empty.<br>
Step 8 : In stack action, Robot arm place the block on under block. Precondition is Block holded by robot arm and no other block on under block.<br>
Step 9 : Define a problem for block world problem.<br> 
Step 10 : Obtain the plan for given problem.<br> 
     
### Program:


### BLOCK WORLD DOMAIN

```
(define (domain blocksworld)
(:requirements :strips :equality)
(:predicates (clear ?x)
             (on-table ?x)
             (arm-empty)
             (holding ?x)
             (on ?x ?y))
(:action pickup
  :parameters (?ob)
  :precondition (and (clear ?ob) (on-table ?ob) (arm-empty))
  :effect (and (holding ?ob) (not (clear ?ob)) (not (on-table ?ob)) 
               (not (arm-empty))))
(:action putdown
  :parameters  (?ob)
  :precondition (and (holding ?ob))
  :effect (and (clear ?ob) (arm-empty) (on-table ?ob) 
               (not (holding ?ob))))
(:action stack
  :parameters  (?ob ?underob)
  :precondition (and  (clear ?underob) (holding ?ob))
  :effect (and (arm-empty) (clear ?ob) (on ?ob ?underob)
               (not (clear ?underob)) (not (holding ?ob))))
(:action unstack
  :parameters  (?ob ?underob)
  
:precondition (and (on ?ob ?underob) (clear ?ob) (arm-empty))
  :effect (and (holding ?ob) (clear ?underob)
               (not (on ?ob ?underob)) (not (clear ?ob)) (not (arm-empty)))))

```

### Input 

### PROBLEM 1

```
(define (problem pb1)
   (:domain blocksworld)
   (:objects a b)
   (:init (on-table a) (on-table b)  (clear a)  (clear b) (arm-empty))
   (:goal (and (on a b))))
```

### PROBLEM 2

```
(define (problem pb2)
   (:domain blocksworld)
   (:objects a b c)
   (:init (on-table a) (on-table b) (on-table c) (clear a) (clear b) (clear c) (arm-empty))
   (:goal (and (on a b) (on b c))))
```

### Output/Plan:

### PROBLEM 1

OUTPUT 1

<img width="338" alt="s1" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/dae8d48d-3014-4c07-b867-4f357e1439cc">

OUTPUT 2

<img width="303" alt="s2" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/655240e7-a3d2-4feb-bd7d-9d4fadb9d77f">


### PROBLEM 2

OUTPUT 1

<img width="323" alt="s3" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/01647848-ad83-4da6-abb1-c621318c87b1">

OUTPUT 2

<img width="302" alt="s4" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/e11f982f-11df-46eb-8a2d-6e9913456624">

OUTPUT 3

<img width="322" alt="s5" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/e610c060-5c2c-4257-aec1-04cbbb6f8650">

OUTPUT 4

<img width="323" alt="s6" src="https://github.com/SmritiManikand/AI_Lab_2023-24/assets/113674204/185622cf-4418-4c81-aa32-9f1185a1cb2a">


### Result:
Thus the plan was found for the initial and goal state of block world problem.
