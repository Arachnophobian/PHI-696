# Project 2

Your second project will require you to answer each of the 10 questions below.  You will be expected to open a pull request with your initial answers by the second class meeting, giving you one week to work on these problems. You and your peers will then have one week to work together to refine your respective initial answers, so they are ready for final submission. Once your pull requests have been reviewed and merged to the development branch, I will review them, then merge to the master branch. 

```
Tip #1: Carefully study the Baader, et. al. selections assigned on bisimulation; it is deceptively subtle, and quite powerful. 
Tip #2: Google is still your friend. So is stackexchange...
Tip #3: Work together to solve these problems, even for initial submissions and when you do, document this in github. 
Tip #4: Work together as a team. 
```

1. Let V be a vocabulary of ALCI consisting of a role name "P". Interpret part_of as "x is a part of y". Using this role name, define the following formulas in this language:
```
  (a)  PP that says that x is a proper part of y
  PP ≡ P ⊓ ¬P¯
  (b)  iPP that says that y is a proper part of x
  iPP ≡ ¬P ⊓ P¯
  (c)  iP that says that y has x as part 
  iP ≡ P¯
  (d)  O that says that x overlaps y
  O ≡ ∃iP.(∃P.⊤)
  (e)  D that says that x and y are disjoint
  D ≡ ¬O
```

2. Use your axioms from question 1 as the basis of an ALCI T-Box. Supplement this T-box with whatever other axioms you like, as well as an A-box, so that you ultimately construct a knowledge base K = (T,A). Provide a _model_ of K. This may be graphical or symbolic or both. 

3. Translate the following first-order logic axioms into ALCI: 
```
(a) ∀x∃y∀z(R(x,y) ∧ R(x,z) ∧ R(y,z))
∃R.(∀R.T) ⊓ ∀R.T
(b) ∃x∀y∃z(R(x,y) ∧ R(x,z) ∧ R(y,z))
∃R¯.(∃R.(∃R¯.T))
(c) ∀y(R(x, y) → ∃x(R(y, x) ∧ ∀y(R(x, y) → A(y))))
∀R.∃R.∀R.A
(d) (∀y)(R(x, y) → A(y)) ∧ (∃y)(R(x, y) ∧ B(y))
(∀R.A) ⊓ (∃R.B
```
4. Provide an interpretation I<sub>1</sub> for ALC and an interpretation I<sub>2</sub> for ALCN - each distinct from any interpretation covered in class so far - and construct a bisimulation that demonstrates ALCN is more expressive than ALC. Use the [mermaid syntax](https://github.com/mermaid-js/mermaid) of markdown to provide a graphical representation of your work. Feel free to use the [mermaid live editor](https://mermaid.live/) when diagramming.

![Do Show](https://user-images.githubusercontent.com/123899465/221320823-8e809616-c35d-46e8-b8b9-da6482ea83f7.png)


ΔI1 = {Dr. Beverley, PHI 697, PHI 329, Tuesday Workshop}

Named IndividualsI:
Dr. BeverleyI = B
PHI 697I = 697
PHI 329I = 329
Tuesday WorkshopI = W

Role Assignments:
t = {(B, 697), (B, 329), (B, W)}


ΔI2 = {Dr. Beverley, PHI 697, PHI 329}

Named IndividualsI:
Dr. BeverleyI2 = B2
PHI2 697I = 697-2
PHI 329I = 329-2

Role Assignments:
t2 = {(B2, 697-2),  (B, 329-2)}

Bisimulation:

ρ = {(B, B2), (697, 697-2), (329, 329-2)}

So B is bisimilar to B2. But we can distinguish them in ALCN by defining the role t as
≥3 ∃t.⊤
in I1
≥2 ∃t2.⊤
in I2



5. Provide an interpretation I<sub>1</sub> for ALC and an interpretation I<sub>2</sub> for ALCN - each distinct from any interpretation covered in class so far - and construct a bisimulation that _does not_ demonstrate ALCN is more expressive than ALC. Use the [mermaid syntax](https://github.com/mermaid-js/mermaid) of markdown to provide a graphical representation of your work. Feel free to use the [mermaid live editor](https://mermaid.live/) when diagramming. 


![Do Not Show](https://user-images.githubusercontent.com/123899465/221320758-a3fa6618-5e46-4661-9db0-2114bb46d5a8.png)


ΔI1 = {Dr. Beverley, PHI 697, PHI 329}

Named IndividualsI:
Dr. BeverleyI = B
PHI 697I = 697
PHI 329I = 329

Role Assignments:
t = {(B, 697), (B, 329), (B, W)}


ΔI2 = {Dr. Beverley, PHI 697, PHI 329}

Named IndividualsI:
Dr. BeverleyI2 = B2
PHI2 697I = 697-2
PHI 329I = 329-2

Role Assignments:
t2 = {(B2, 697-2),  (B, 329-2)}

Bisimulation:

ρ = {(B, B2), (697, 697-2), (329, 329-2)}

So B is bisimilar to B2. The ALCN definitions are
≥2 ∃m.⊤
in I1
≥2 ∃m2.⊤
in I2


6. Explain the difference - using natural language - between the description logic expressions:
  ```
  (a) ∃r.C and ∀r.C
    ∃r.C can be read as: "The set of things with a certain Telation that belong to a certain Class."
    ∀r.C can be read as: "The set of things with a certain relation that belong to only one certain Class."
      
      In the first case, the class is ONE OF the classes to which the set of things belong - in the second, it is the ONLY     class to which the set of things belongs.
  
  (b) ∃r-.C and ∀r-.C
    ∃r-.C can be read as: "The set of things with the opposite* of a certain Relation that belong to a certain Class."
    ∀r-.C can be read as: "The set of things with the opposite* of a Relation that belong to only one certain Class."
    
    This mirrors the above: the difference between the first case and the second is that the second restricts the membership of the set of things to one class. 
    *Note - I used "opposite" and not "inverse" because I think opposite sounds more appropriate in natural language.
    
  (c) <=nr and <=nr.C
    <=nr can be read as:"The Relation holds for all the number of elements in the set."
    <=nr.C can be read as: "The Relation holds for no more than the number of elements in the set which belong to a certain Class."
    
    The second is more restrictive; we aren't focusing on *all* the elements of the set which has this particular role, but only those which are members of a particular class.
    
  (d) ∃r-.C and ∃r-.{a} 
    ∃r-.C can be read as: "The set of things with the opposite* of a certain Relation that belong to a certain Class."
    ∃r-.{a} can be read as: The set of things with the opposite* of a certain Relation that belong to a set with only one member/element."
    
    In the first case, as above, we're talking about everything within a class that has the opposite of some role. But in the second case we are talking about a set with only one thing in it. In a way, we're just describing whatever that thing is in terms of it having the opposite of a particular role (which seems weird, but might be a useful way of identifying something particular which we would like to exclude).
    
    *Note - I used "opposite" and not "inverse" because I think opposite sounds more appropriate in natural language.
  
  
```

7. There is a delightfully helpful subreddit called "ELI5" which stands for something like "explain it like I'm 5" where users post conceptually challenging questions and other users attempt to provide explanations in simple, jargon-free, terms that presumably a 5 year-old could understand. Using this as a model, explain the _finite model property_. Be sure to provide a simple example and explain when the property might be important, and when it is not so important. 

The Finite Model Property involves three things; rules, games, and pieces. I want to make a game, but I want my game to be good, so I need to make it so you can *win* my game. This means the game has to end sometime. To make sure it ends, I need a set of rules for my game. But you can't win a game with *only* rules... you need pieces to be able to play! So, when I make my rules, I have to make sure that you can use the pieces, in accordance with the rules, to win the game. 
But, if I'm making a really hard game, I don't have time to also make peices. But how do I know what pieces you can buy that will work to win the game? What I can do is make up some MORE rules that say that you can't use just any pieces; you have to use specific ones. And I can make these extra rules really specific, and instead of telling you what pieces definitely will work, I can tell you what pieces definitely *won't* work.

Of course, what if the game is so much fun that, actually, I don't want it to end? Well, then I don't need those extra rules.


8. Following up on the preceding , explain the _tree model property_. Be sure to provide a simple example and explain when the property might be important, and when it is not so important. 

Let's say I have a strange kickball. Every time I kick it the outside of it slides off, like a snake shedding its skin. Each time the outside slides off, the ball changes; if it was light it becomes heavy, and if it was heavy it becomes light. 
If I want to tell you about my kickball, I can describe it just like I did; you don't know if the ball is heavy or light right now, just that it will be changed and the outside will slide off when you kick it.
But, instead, I could describe it by first telling you "This ball is heavy! When you kick it though, the outside will slide off and it'll be light. And if you kick it again, the outside will slide off and it'll be heavy."
If I did it this second way, I'd be describing my kickball using the tree model property; in both cases, the process continues over and over, always the same, but in the second one I'm telling you where we start.




9. Open the Protege editor and create object properties for each of the role names that you constructed in question 1. You should have at least 6 object properties. Assert in the editor that P is a sub-property of O, that P is transitive, and that O is symmetric. Next, add individuals - a, b, c - to the file and assert that c is part of a and that c overlaps b. Running the reasoner should reveal - highlighted in yellow if you select the individual c - that c overlaps a. Using the discussion in the selections from chapter 4 of the Baader, et. al. text as a guide, explain how the tableau algorithm is generating this inference. Also, provide a screenshot of the results of your reasoner run with c highlighted. 

10. Following up on your work in question 9, adjust/add/remove/etc. object properties and individuals in your Protege file so that when you run a reasoner in Protege, you return the following consequences: 
```
  (a) a is a proper part of b and disjoint from e
  (b) a overlaps c
  (c) a is part of b, b is part of f, and a is part of f
  (e) There are no parts between a and g in common
```
Provide a screenshot of your results here. 
