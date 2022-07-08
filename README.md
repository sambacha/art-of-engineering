# Engineering Polemic: The art of

> portions taken from:
> https://github.com/charlax/professional-programming/tree/master/antipatterns

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table of Contents

- [Engineering Polemic: The art of](#engineering-polemic-the-art-of)
  - [Table of Contents](#table-of-contents)
    - [Antipatterns](#antipatterns)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## Principles

- [Zen of Python](http://files.catwell.info/misc/mirror/zen-of-python.txt)
- [The Arch Way](https://wiki.archlinux.org/index.php/The_Arch_Way)
- [Unix Philosophies](http://www.faqs.org/docs/artu/ch01s06.html)
- [Suckless Philosophy](http://suckless.org/philosophy)

- Prototyping
- Separation of Concerns
- Services Oriented Architectures (see [Yegge](http://files.catwell.info/misc/mirror/steve-yegge-google-amazon.txt))


### Antipatterns

This is a list of antipatterns.

- [Code antipatterns](./Omnibus/Antipatterns/code-antipatterns.md)
- [Python antipatterns](./Omnibus/Antipatterns/python-antipatterns.md)
- [SQLAlchemy antipatterns](./Omnibus/Antipatterns/sqlalchemy-antipatterns.md)
- [Error handling antipatterns](./Omnibus/Antipatterns/error-handling-antipatterns.md)
- [Tests antipatterns](./Omnibus/Antipatterns/tests-antipatterns.md)


## Map of Repo

```
Omnibus/
├── ART_OF_COLD_SHOWERS.md
├── Antipatterns
│   ├── code-antipatterns.md
│   ├── database-antipatterns.md
│   ├── error-handling-antipatterns.md
│   ├── mvcs-antipatterns.md
│   ├── scalability-antipatterns.md
│   ├── sqlalchemy-antipatterns.md
│   ├── sqlalchemy-examples
│   │   └── exists.py
│   └── tests-antipatterns.md
├── Art_of
│   ├── ENGINEERING_ART_OF.md
│   ├── ENGINEERING_ART_OF_APL.md
│   ├── ENGINEERING_ART_OF_DEBUGGING.md
│   ├── ENGINEERING_ART_OF_IDEs.md
│   └── ENGINEERING_ART_OF_software_project_management.md
├── DISTRIBUTED_SYSTEMS.md
├── Design
│   └── On_Weaponised_Design.md
├── MISC_redux_is_a_half_pattern.md
└── MISC_thoughts.md
```


<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


# Polemic of Engineering


💊 🌲  📚

- [Polemic of Engineering](#polemic-of-engineering)
  * [Table of Contents](#table-of-contents)
      - [Engineering Compendium](#engineering-compendium)
  * [Programming Language Theory](#programming-language-theory)
  * [Type Theory](#type-theory)
    + [Books](#books)
    + [Papers](#papers)
    + [Videos](#videos)
    + [Subtopics](#subtopics)
  * [Programming Languages](#programming-languages)
    + [Books](#books-1)
    + [Papers](#papers-1)
  * [Compiler Construction](#compiler-construction)
    + [Books](#books-2)
    + [Papers](#papers-2)
    + [Videos](#videos-1)
  * [Runtime systems](#runtime-systems)
    + [Books](#books-3)
    + [Papers](#papers-3)
  * [Functional Programming](#functional-programming)
    + [Books](#books-4)
      - [Papers](#papers-4)
    + [Videos](#videos-2)
    + [Category Theory](#category-theory)
      - [Books](#books-5)
      - [Journals](#journals)
      - [Subtopics](#subtopics-1)
    + [Mathematics](#mathematics)
      - [Mathematical Literacy/Thinking](#mathematical-literacy-thinking)
      - [Algebra](#algebra)
    + [Other collections](#other-collections)
      - [Certification is useless](#certification-is-useless)
      - [Motivated teams:](#motivated-teams-)
      - [Happiness Metric.](#happiness-metric)
      - [A Role-Based Empirical Process Modeling Environment.](#a-role-based-empirical-process-modeling-environment)
      - [Organizational Patterns of Agile Software](#organizational-patterns-of-agile-software)
      - [SIMULA 67 Common Base Language. Norwegian](#simula-67-common-base-language-norwegian)
      - [Borland Software Craftsmanship: A New Look at Process,](#borland-software-craftsmanship--a-new-look-at-process-)
      - [Agile Software Development with Scrum. Pearson,](#agile-software-development-with-scrum-pearson-)
      - [Software in 30 Days: How Agile Managers Beat the Odds, Delight](#software-in-30-days--how-agile-managers-beat-the-odds--delight)
      - [A Development Process Generative Pattern Language. In James O.](#a-development-process-generative-pattern-language-in-james-o)
      - [A Laboratory for Teaching Object-Oriented Thinking. Proceedings of](#a-laboratory-for-teaching-object-oriented-thinking-proceedings-of)
      - [Architecture and the Child Within. Games versus Play,](#architecture-and-the-child-within-games-versus-play-)
      - [Objects as mental models.](#objects-as-mental-models)
      - [The Humane Interface: New Directions for Designing Interactive](#the-humane-interface--new-directions-for-designing-interactive)
      - [A Laboratory for Teaching Object-Oriented Thinking. Proceedings of](#a-laboratory-for-teaching-object-oriented-thinking-proceedings-of-1)
      - [Comparative Case Study on the Effect of Test-Driven](#comparative-case-study-on-the-effect-of-test-driven)
      - [Does Test-Driven Development Improve the Program Code? Alarming results from a Comparative Case Study.](#does-test-driven-development-improve-the-program-code--alarming-results-from-a-comparative-case-study)
      - [Segue.](#segue)
      - [Toyota automation:](#toyota-automation-)
      - [Research on DCI by Héctor Valdecantos.](#research-on-dci-by-h-ctor-valdecantos)
      - [Study on Code Comprehension: Data Context Interaction Compared to Classical Object Oriented.](#study-on-code-comprehension--data-context-interaction-compared-to-classical-object-oriented)
      - [Long deliberation.](#long-deliberation)
      - [Last Responsible Moment. Glenn Ballard. Positive versus negative iteration in](#last-responsible-moment-glenn-ballard-positive-versus-negative-iteration-in)
      - [The Quality without a Name. Christopher Alexander. The Timeless Way of Building.](#the-quality-without-a-name-christopher-alexander-the-timeless-way-of-building)
      - [Mob Programming.](#mob-programming)
      - [Organizational Learning. Joop Swieringa and Andre Wierdsma. Becoming a Learning](#organizational-learning-joop-swieringa-and-andre-wierdsma-becoming-a-learning)
      - [Organization: Beyond the Learning Curve. Addison-Wesley, 1992.](#organization--beyond-the-learning-curve-addison-wesley--1992)
      - [Stable Teams:](#stable-teams-)
      - [The Ten Bulls.](#the-ten-bulls)
      - [The Design Movement:](#the-design-movement-)
  * [About the efficient reduction of lambda terms](#about-the-efficient-reduction-of-lambda-terms)
  * [The optimal implementation of functional programming languages](#the-optimal-implementation-of-functional-programming-languages)


## Polemic: Lotus Eaters

> Chapter 5 - Lotus Eaters, Blue Route, *Ulysses*

- [Lotus Eaters](#table-of-contents)
    - [Engineering Compendium](#engineering-compendium)
    - [Certification is useless](#certification-is-useless)
    - [Motivated teams:](#motivated-teams)
    - [Happiness Metric.](#happiness-metric)
    - [A Role-Based Empirical Process Modeling Environment.](#a-role-based-empirical-process-modeling-environment)
    - [Organizational Patterns of Agile Software](#organizational-patterns-of-agile-software)
    - [SIMULA 67 Common Base Language. Norwegian](#simula-67-common-base-language-norwegian)
    - [Borland Software Craftsmanship: A New Look at Process,](#borland-software-craftsmanship-a-new-look-at-process)
    - [Agile Software Development with Scrum. Pearson,](#agile-software-development-with-scrum-pearson)
    - [Software in 30 Days: How Agile Managers Beat the Odds, Delight](#software-in-30-days-how-agile-managers-beat-the-odds-delight)
    - [A Development Process Generative Pattern Language. In James O.](#a-development-process-generative-pattern-language-in-james-o)
    - [A Laboratory for Teaching Object-Oriented Thinking. Proceedings of](#a-laboratory-for-teaching-object-oriented-thinking-proceedings-of)
    - [Architecture and the Child Within. Games versus Play,](#architecture-and-the-child-within-games-versus-play)
    - [Objects as mental models.](#objects-as-mental-models)
    - [The Humane Interface: New Directions for Designing Interactive](#the-humane-interface-new-directions-for-designing-interactive)
    - [A Laboratory for Teaching Object-Oriented Thinking. Proceedings of](#a-laboratory-for-teaching-object-oriented-thinking-proceedings-of-1)
    - [Comparative Case Study on the Effect of Test-Driven](#comparative-case-study-on-the-effect-of-test-driven)
    - [Does Test-Driven Development Improve the Program Code? Alarming results from a Comparative Case Study.](#does-test-driven-development-improve-the-program-code-alarming-results-from-a-comparative-case-study)
    - [Segue.](#segue)
    - [Toyota automation:](#toyota-automation)
    - [Research on DCI by Héctor Valdecantos.](#research-on-dci-by-h%C3%A9ctor-valdecantos)
    - [Study on Code Comprehension: Data Context Interaction Compared to Classical Object Oriented.](#study-on-code-comprehension-data-context-interaction-compared-to-classical-object-oriented)
    - [Long deliberation.](#long-deliberation)
    - [Last Responsible Moment. Glenn Ballard. Positive versus negative iteration in](#last-responsible-moment-glenn-ballard-positive-versus-negative-iteration-in)
    - [The Quality without a Name. Christopher Alexander. The Timeless Way of Building.](#the-quality-without-a-name-christopher-alexander-the-timeless-way-of-building)
    - [Mob Programming.](#mob-programming)
    - [Organizational Learning. Joop Swieringa and Andre Wierdsma. Becoming a Learning](#organizational-learning-joop-swieringa-and-andre-wierdsma-becoming-a-learning)
    - [Organization: Beyond the Learning Curve. Addison-Wesley, 1992.](#organization-beyond-the-learning-curve-addison-wesley-1992)
    - [Stable Teams:](#stable-teams)
    - [The Ten Bulls.](#the-ten-bulls)
    - [The Design Movement:](#the-design-movement)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

#### Engineering Compendium

- [Engineering Compendium](#engineering-compendium)
- [Certification is useless](#certification-is-useless)
- [Motivated teams:](#motivated-teams-)
- [Happiness Metric.](#happiness-metric)
- [A Role-Based Empirical Process Modeling Environment.](#a-role-based-empirical-process-modeling-environment)
- [Organizational Patterns of Agile Software](#organizational-patterns-of-agile-software)
- [SIMULA 67 Common Base Language. Norwegian](#simula-67-common-base-language-norwegian)
- [Borland Software Craftsmanship: A New Look at Process,](#borland-software-craftsmanship--a-new-look-at-process-)
- [Agile Software Development with Scrum. Pearson,](#agile-software-development-with-scrum-pearson-)
- [Software in 30 Days: How Agile Managers Beat the Odds, Delight](#software-in-30-days--how-agile-managers-beat-the-odds--delight)
- [A Development Process Generative Pattern Language. In James O.](#a-development-process-generative-pattern-language-in-james-o)
- [A Laboratory for Teaching Object-Oriented Thinking. Proceedings of](#a-laboratory-for-teaching-object-oriented-thinking-proceedings-of)
- [Architecture and the Child Within. Games versus Play,](#architecture-and-the-child-within-games-versus-play-)
- [Objects as mental models.](#objects-as-mental-models)
- [The Humane Interface: New Directions for Designing Interactive](#the-humane-interface--new-directions-for-designing-interactive)
- [A Laboratory for Teaching Object-Oriented Thinking. Proceedings of](#a-laboratory-for-teaching-object-oriented-thinking-proceedings-of-1)
- [Comparative Case Study on the Effect of Test-Driven](#comparative-case-study-on-the-effect-of-test-driven)
- [Does Test-Driven Development Improve the Program Code? Alarming results from a Comparative Case Study.](#does-test-driven-development-improve-the-program-code--alarming-results-from-a-comparative-case--study)
- [Segue.](#segue)
- [Toyota automation:](#toyota-automation-)
- [Research on DCI by Héctor Valdecantos.](#research-on-dci-by-h-ctor-valdecantos)
- [Study on Code Comprehension: Data Context Interaction Compared to Classical Object Oriented.](#study-on-code-comprehension--data-context-interaction-compared-to-classical-object-oriented)
- [Long deliberation.](#long-deliberation)
- [Last Responsible Moment. Glenn Ballard. Positive versus negative iteration in](#last-responsible-moment-glenn-ballard-positive-versus-negative-iteration-in)
- [The Quality without a Name. Christopher Alexander. The Timeless Way of Building.](#the-quality-without-a-name-christopher-alexander-the-timeless-way-of-building)
- [Mob Programming.](#mob-programming)
- [Organizational Learning. Joop Swieringa and Andre Wierdsma. Becoming a Learning](#organizational-learning-joop-swieringa-and-andre-wierdsma-becoming-a-learning)
- [Organization: Beyond the Learning Curve. Addison-Wesley, 1992.](#organization--beyond-the-learning-curve-addison-wesley--1992)
- [Stable Teams:](#stable-teams-)
- [The Ten Bulls.](#the-ten-bulls)
- [The Design Movement:](#the-design-movement-)
- [Differential Testing For Software](https://www.cs.swarthmore.edu/~bylvisa1/cs97/f13/Papers/DifferentialTestingForSoftware.pdf)

<!-- Programming Language Theory sourced from https://steshaw.org/plt/ on 2022.05.10 -->
## Programming Language Theory

Learning about _Programming Language Theory_ can be a tough journey, particularly for programming practitioners who haven’t studied it formally. This resource is here to help. Please feel free to get in touch if you have ideas for improvement.

#### 💡 Top Tips

For a quick course in Type Theory, Philip Wadler recommends: _[Types and Programming Languages](http://www.cis.upenn.edu/~bcpierce/tapl/)_, _[Proofs and Types](http://www.paultaylor.eu/stable/Proofs+Types.html)_, followed by _[Advanced Topics in Types and Programming Languages](https://www.cis.upenn.edu/~bcpierce/attapl/)_.

See also Daniel Gratzer’s [Learn Type Theory](https://github.com/jozefg/learn-tt) and Darryl McAdams’s [So you want to learn type theory](https://web.archive.org/web/20190213100051/http://purelytheoretical.com/sywtltt.html).

## Type Theory

### Books

-   [PLFA](https://plfa.github.io/) - Programming Language Foundations in Agda - [Philip Wadler](https://github.com/wadler), [Wen Kokke](https://github.com/wenkokke)
-   [SF](http://www.cis.upenn.edu/~bcpierce/sf/) - Software Foundations - Benjamin C. Pierce et al.
-   [TAPL](http://www.cis.upenn.edu/~bcpierce/tapl/) - Types and Programming Languages - Benjamin C. Pierce
-   [PROT](http://www.paultaylor.eu/stable/Proofs+Types.html) Proofs and Types - Jean-Yves Girard, Yves Lafont and Paul Taylor - 1987-90 [pdf](http://www.paultaylor.eu/stable/prot.pdf)
-   [PFPL](http://www.cs.cmu.edu/~rwh/pfpl/) - Practical Foundations for Programming Languages (Second Edition) - Robert Harper [Online preview edition](http://www.cs.cmu.edu/~rwh/pfpl/2nded.pdf)
-   [ATTAPL](http://www.cis.upenn.edu/~bcpierce/attapl/) - Advanced Topics in Types and Programming Languages - Edited by Benjamin C. Pierce
-   [CPDT](http://adam.chlipala.net/cpdt/) - Certified Programming with Dependent Types - Adam Chlipala
-   [SEwPR](http://mitpress.mit.edu/books/semantics-engineering-plt-redex) - Semantics Engineering with PLT Redex - Matthias Felleisen, Robby Findler, and Matthew Flatt. [Redex](http://redex.racket-lang.org/)
-   [HoTT](http://homotopytypetheory.org/book/) - Homotopy Type Theory, Univalent Foundations of Mathematics
-   [Coq’Art](http://www.labri.fr/perso/casteran/CoqArt/index.html) Interactive Theorem Proving and Program Development, Coq’Art: The Calculus of Inductive Constructions - Yves Bertot, Pierre Castéran.
-   [TTFP](http://www.cs.kent.ac.uk/people/staff/sjt/TTFP/) - Type Theory and Functional Programming - Simon Thompson, 1991
-   [PiMLTT](http://www.cse.chalmers.se/research/group/logic/book/) - Programming in Martin-Löf’s Type Theory, An Introduction - Bengt Nordström, Kent Petersson, Jan M. Smith
-   Using, Understanding, and Unravelling The OCaml Language — An introduction [pdf](http://pauillac.inria.fr/~remy/cours/appsem/ocaml.pdf)
-   Polymorphic typing of an algorithmic language (PhD Thesis) - Xavier Leroy [pdf](http://gallium.inria.fr/~xleroy/publi/phd-thesis.pdf)
-   [ATP](http://www.cl.cam.ac.uk/~jrh13/atp/) - Handbook of Practical Logic and Automated Reasoning - John Harrison
-   Basic Simple Type Theory - J. Roger Hindley [pdf](http://mathtrielhighschool.files.wordpress.com/2011/08/number-theory.pdf) [paperback@booko](http://booko.com.au/9780521054225/Basic-Simple-Type-Theory)
-   [Lambda Calculus and Combinators](http://www.cambridge.org/us/academic/subjects/computer-science/programming-languages-and-applied-logic/lambda-calculus-and-combinators-introduction-2nd-edition) [pdf](http://pds14.egloos.com/pds/200901/16/93/Lambda-Calculus_and_Combinators.pdf) — J. Roger Hindley and Jonathan P. Seldin
-   [Semantics with Applications: An Appetizer](http://www.daimi.au.dk/~bra8130/Wiley_book/wiley.pdf) — Hanne Riis Nielson, Flemming Nielson
-   An Introduction to Lambda Calculi for Computer Scientists - Chris Hankin
-   The Definition of Standard ML (Revised) - Milner, Fofte, Harper, and MacQueen
-   [The Definition of Standard ML (1990) and Commentary on Standard ML (1991)](http://www.itu.dk/people/tofte/publ/1990sml/1990sml.html) [definition (pdf)](http://www.itu.dk/people/tofte/publ/1990sml/1990sml.pdf) [commentary (pdf)](http://www.itu.dk/people/tofte/publ/1990sml/1991commentaryBody.pdf)
-   [Programs and Proofs](http://ilyasergey.net/pnp/) — Ilya Sergey [pdf](http://ilyasergey.net/pnp/pnp.pdf)
-   [Type Theory and Formal Proof: An Introduction](https://www.amazon.com/Type-Theory-Formal-Proof-Introduction/dp/110703650X) — Rob Nederpelt, Herman Geuvers
-   [Lectures on the Curry-Howard Isomorphism (pdf)](http://disi.unitn.it/~bernardi/RSISE11/Papers/curry-howard.pdf)

### Papers

-   [A Tutorial Implementation of a Dependently Typed Lambda Calculus](http://www.andres-loeh.de/LambdaPi/) — Andres Löh, Conor McBride and Wouter Swierstra [pdf](http://www.andres-loeh.de/LambdaPi/LambdaPi.pdf). Previously published as [Simply Easy](http://strictlypositive.org/Easy.pdf).
-   [ΠΣ: Dependent Types without the Sugar](https://www.andres-loeh.de/PiSigma/PiSigma.pdf) - Thorsten Altenkirch, Nils Anders Danielsson, Andres Löh, and Nicolas Oury
-   [Lambda Calculi with Types](http://ttic.uchicago.edu/~dreyer/course/papers/barendregt.pdf) — Henk Barendregt
-   [Intuitionistic Type Theory](http://www.csie.ntu.edu.tw/~b94087/ITT.pdf)

### Videos

-   [OPLSS — Oregon Programming Language Summer School](http://www.cs.uoregon.edu/research/summerschool/)
    -   [OPLSS 2019 — Foundations of Probabilistic Programming and Security](https://www.cs.uoregon.edu/research/summerschool/summer19/topics.php)
    -   [OPLSS 2018 — Parallelism and Concurrency](https://www.cs.uoregon.edu/research/summerschool/summer18/topics.php)
    -   [OPLSS 2017 — A Spectrum of Types](https://www.cs.uoregon.edu/research/summerschool/summer17/topics.php)
    -   [OPLSS 2016 — Types, Logic, Semantics, and Verification](http://www.cs.uoregon.edu/research/summerschool/summer16/curriculum.php)
    -   [OPLSS 2015 — Types, Logic, Semantics, and Verification](http://www.cs.uoregon.edu/research/summerschool/summer15/curriculum.html)
    -   [OPLSS 2014 — Types, Logic, Semantics, and Verification](http://www.cs.uoregon.edu/research/summerschool/summer14/curriculum.html)
    -   [OPLSS 2013 — Types, Logic, and Verification](http://www.cs.uoregon.edu/research/summerschool/summer13/curriculum.html)
    -   [OPLSS 2012 — Logic, Languages, Compilation, and Verification](http://www.cs.uoregon.edu/research/summerschool/summer12/curriculum.html)
    -   [OPLSS 2011 — Types, Semantics and Verification](http://www.cs.uoregon.edu/research/summerschool/summer11/curriculum.html)
    -   [OPLSS 2010 — Logic, Languages, Compilation, and Verification](http://www.cs.uoregon.edu/research/summerschool/summer10/curriculum.html)
    -   [Archives 2002-2018](https://www.cs.uoregon.edu/research/summerschool/archives.html)
-   [ICFP 2012 Monday keynote. Conor McBride: Agda-curious?](https://youtu.be/XGyJ519RY6Y)

### Subtopics

-   [Higher Type Theory](https://steshaw.org/plt/higher-type-theory/)
-   [Module Systems](https://steshaw.org/plt/module-systems/)
-   [Effect Systems](https://steshaw.org/plt/effect-systems/)

## Programming Languages

### Books

-   [DCPL](http://dcpl.mit.edu/) - Design Concepts in Programming Languages – Franklyn Turbak and David Gifford, 2008
-   [CTM](http://www.info.ucl.ac.be/~pvr/book.html) - Concepts, Techniques and Models of Computer Programming, Peter Van Roy and Seif Haridi
-   [EOPL](http://www.eopl3.com/) - Essentials of Programming Languages, 3rd Edition - Daniel P. Friedman
-   [PLAI-2nd](http://cs.brown.edu/courses/cs173/2012/book/) - Programming Languages: Application and Interpretation - Shriram Krishnamurthi [course with videos](http://cs.brown.edu/courses/cs173/2012/) [PLAI-1st](http://cs.brown.edu/~sk/Publications/Books/ProgLangs/)
-   [PAIP](http://www.norvig.com/paip.html) Paradigms of Artificial Intelligence Programming: Case Studies in Common Lisp - Peter Norvig, 1992
-   [PLP](http://cs.rochester.edu/u/scott/pragmatics/) Programming Language Pragmatics - Michael L. Scott
-   [FSPL](https://mitpress.mit.edu/books/formal-semantics-programming-languages) The Formal Semantics of Programming Languages - Glynn Winskel

### Papers

-   [An argument against call/cc](http://okmij.org/ftp/continuations/against-callcc.html) — Oleg Kiselyov

## Compiler Construction

### Books

-   [MinCaml](http://esumii.github.io/min-caml/index-e.html) - A Crash Course for the MinCaml Compiler
-   [MCIiML](http://www.cs.princeton.edu/~appel/modern/ml/) Modern Compiler Implementation in ML - Andrew W. Appel
-   [pj-lester-book](http://research.microsoft.com/en-us/um/people/simonpj/papers/pj-lester-book/) Implementing functional languages: a tutorial - Simon Peyton Jones and David Lester, 1992
-   [slpj-book-1987](http://research.microsoft.com/en-us/um/people/simonpj/papers/slpj-book-1987/) - The Implementation of Functional Programming Languages - Simon Peyton Jones - 1987
-   [MCD-2e](http://www.dickgrune.com/Books/MCD_2nd_Edition/) Modern Compiler Design, Second Edition — Dick Grune et al.
-   EaC-2e Engineering a Compiler, 2nd Edition, Cooper and Torczon
-   [Compiler Construction](http://www.ethoberon.ethz.ch/WirthPubl/CBEAll.pdf), Niklaus Wirth
-   [DragonBook](http://dragonbook.stanford.edu/) - “The Dragon Book” Compilers: Principles, Techniques, and Tools
-   [LiSP](http://www.cambridge.org/us/academic/subjects/computer-science/programming-languages-and-applied-logic/lisp-small-pieces) - Lisp in Small Pieces - Christian Queinnec
-   [CwC](http://www.cambridge.org/us/academic/subjects/computer-science/programming-languages-and-applied-logic/compiling-continuations) Compiling with Continuations - Andrew W. Appel
-   [Static Program Analysis](https://cs.au.dk/~amoeller/spa/spa.pdf), Anders Møller and Michael I. Schwartzbach
-   [List of compiler books at the GCC Wiki](http://gcc.gnu.org/wiki/ListOfCompilerBooks)

### Papers

-   [An Incremental Approach to Compiler Construction](http://scheme2006.cs.uchicago.edu/11-ghuloum.pdf), Abdulaziz Ghuloum
-   [A Nanopass Framework for Compiler Education](http://www.cs.indiana.edu/~dyb/pubs/nano-jfp.pdf), Dipanwita Sarkar, Oscar Waddell, R. Kent Dybvig
-   [A Nanopass Framework for Commercial Compiler Development](http://andykeep.com/pubs/dissertation.pdf), [Andrew W. Keep](http://andykeep.com/)
-   [ZINC](http://caml.inria.fr/pub/papers/xleroy-zinc.pdf) - The ZINC experiment, an economical implementation of the ML language - Xavier Leroy (Technical Report) [more OCaml papers](http://caml.inria.fr/about/papers.en.html)

### Videos

-   [Stanford - Compilers](https://online.stanford.edu/course/compilers-0) - Alex Aiken

## Runtime systems

### Books

-   [The Garbage Collection Handbook, The Art of Automatic Memory Management](http://gchandbook.org/) — Richard Jones, Antony Hosking, Eliot Moss, 2011.

### Papers

-   [Debunking the ‘Expensive Procedure Call’ Myth, or, Procedure Call Implementations Considered Harmful, or, Lambda: The Ultimate GOTO](https://web.archive.org/web/20180406191621/http://library.readscheme.org/page1.html) — Guy Lewis Steele, Jr. (1977) [pdf](https://web.archive.org/web/20180130013734/http://repository.readscheme.org/ftp/papers/ai-lab-pubs/AIM-443.pdf)

## Functional Programming

### Books

-   [Bird and Wadler](http://usi-pl.github.io/lc/sp-2015/doc/Bird_Wadler.%20Introduction%20to%20Functional%20Programming.1ed.pdf) - Introduction to Functional Programming, 1st Edition - Bird and Wadler
-   [AoP](http://www.amazon.com/books/dp/013507245X) - The Algebra of Programming - Richard Bird, Oege de Moor
-   [Programming in Haskell](http://www.cs.nott.ac.uk/~gmh/book.html) — Graham Hutton (2007)
-   [RWH](http://book.realworldhaskell.org/) - Real World Haskell - Bryan O’Sullivan, Don Stewart, and John Goerzen
-   [FPiS](http://www.manning.com/bjarnason/) - Functional Programming in Scala - Paul Chiusano and Rúnar Bjarnason
-   [SICP](http://mitpress.mit.edu/sicp/), Structure and Interpretation of Computer Programs, by Abelson, Sussman, and Sussman
-   [PCPH](http://chimera.labs.oreilly.com/books/1230000000929) - Parallel and Concurrent Programming in Haskell - Simon Marlow
-   [RWOC](https://realworldocaml.org/) - Real World OCaml - Jason Hickey, Anil Madhavapeddy, and Yaron Minsky
-   [Developing Applications With OCaml](http://caml.inria.fr/pub/docs/oreilly-book/index.html) — Emmanuel Chailloux, Pascal Manoury and Bruno Pagano (2000)
-   [BTLS](http://www.ccs.neu.edu/home/matthias/BTLS/) - The Little Schemer - Daniel P. Friedman, Matthias Felleisen
-   [BTSS](http://www.ccs.neu.edu/home/matthias/BTSS/) - The Seasoned Schemer - Daniel P. Friedman, Matthias Felleisen
-   [BTML](http://www.ccs.neu.edu/home/matthias/BTML/) - The Little MLer - Matthias Felleisen, Daniel P. Friedman
-   [The Reasoned Schemer](http://minikanren.org/) and miniKanren
-   [HTDP](http://www.htdp.org/) - How to Design Programs - Matthias Felleisen, Robert Findler, Matthew Flatt, Shriram Krishnamurthi
-   [HR](http://homepages.cwi.nl/~jve/HR/) - The Haskell Road to Logic, Maths and Programming - 2nd Ed. - Kees Doets, Jan van Eijck [pdf](http://fldit-www.cs.uni-dortmund.de/~peter/PS07/HR.pdf)
-   A Book of Abstract Algebra - 2nd Ed. - Charles C. Pinter [booko](http://booko.com.au/9780486474175/Book-of-Abstract-Algebra)
-   Purely Functional Data Structures - Chris Okasaki [phd-thesis in pdf](http://www.cs.cmu.edu/~rwh/theses/okasaki.pdf) [paperback@booko](http://booko.com.au/9780521663502/Purely-Functional-Data-Structures) [More purely functional data structures](http://cstheory.stackexchange.com/questions/1539/whats-new-in-purely-functional-data-structures-since-okasaki)

#### Papers

-   [Lambda Papers](http://library.readscheme.org/page1.html) - Lambda: The Ultimate Imperative/Declarative/GOTO - Guy Steele and Gerald Sussman
-   [Exploring Generic Haskell](http://www.andres-loeh.de/ExploringGH.pdf) (PhD thesis) - [Andres Löh](http://www.andres-loeh.de/). This an epic, accessible, book-length PhD on datatype generic programming.
-   ICFP accepted papers
    -   [2019](https://github.com/llelf/icfp2019-papers)
    -   [2018](https://icfp18.sigplan.org/track/icfp-2018-papers#program), [video playlist](https://www.youtube.com/watch?v=Z3vr5xylMCE&list=PLnqUlCo055hVknu7QAW_RUZRmRZWXmnvv)
    -   [2017](https://github.com/gasche/icfp2017-papers), [video playlist](https://www.youtube.com/watch?v=RoddXtl8SU8&list=PLnqUlCo055hW7kU-SBQEhC_87etA5Gqlq)
    -   [2016](https://github.com/gasche/icfp2016-papers), [video playlist](https://www.youtube.com/watch?v=EpifLmPM1L0&list=PLnqUlCo055hV-Yb_88YYUC2ucaBKCWCsa)
    -   [2015](https://github.com/mpickering/icfp2015-papers), [by session](http://icfpconference.org/icfp2015/toc.html), [video playlist](https://www.youtube.com/watch?v=PI99A08Y83E&list=PLnqUlCo055hWNtUo1Haoq347VhCqIjs7u)
    -   [2014](https://github.com/yallop/icfp2014-papers)
    -   [2013](https://github.com/gasche/icfp2013-papers)
    -   [2012](https://github.com/technogeeky/icfp12-paper-links)

### Videos

-   [C9 Lectures: Dr. Erik Meijer - Functional Programming Fundamentals](http://channel9.msdn.com/Series/C9-Lectures-Erik-Meijer-Functional-Programming-Fundamentals)
-   [C9 Lectures: Dr. Ralf Lämmel - Going Bananas + Advanced Functional Programming](http://channel9.msdn.com/Tags/ralf-laemmel)
-   [Datatype-Generic Programming in Haskell](http://skillsmatter.com/podcast/home/a-haskell-lecture-with-leading-expert-andres-loh) - [Andres Löh](http://www.andres-loeh.de/) - [slides in pdf](http://www.andres-loeh.de/GP-ITB.pdf)

### Category Theory

> Philip Wadler’s advice here is “read Pierce for motivation, Mac Lane for the presentation of the maths”.

#### Books

-   [Cakes, Custard and Category Theory: Easy recipes for understanding complex maths](http://www.amazon.com/Cakes-Custard-Category-Theory-understanding-ebook/dp/B00TA8SIV6) — [Eugenia Cheng](http://eugeniacheng.com/)
-   Category Theory, Steve Awodey. [notes](https://www.andrew.cmu.edu/course/80-413-713/notes/)
-   Basic Category Theory for Computer Scientists - Benjamin C. Pierce. Previously available in a draft entitled [A taste of category theory for computer scientists](http://repository.cmu.edu/cgi/viewcontent.cgi?article=2846&context=compsci)
-   [Categories for the Working Mathematician](http://www.maths.ed.ac.uk/~aar/papers/maclanecat.pdf) — Saunders Mac Lane
-   [Conceptual Mathematics](http://www.cambridge.org/us/academic/subjects/mathematics/logic-categories-and-sets/conceptual-mathematics-first-introduction-categories-2nd-edition) A First Introduction to Categories, 2nd Edition - F. William Lawere and Stephen H. Schanuel
-   [Category Theory for the Sciences](http://category-theory.mitpress.mit.edu/) — David I. Spivak. Previously available in a draft entitled [Category Theory for Scientists](http://math.mit.edu/~dspivak/CT4S.pdf)
-   [CTCS-2nd](http://www.math.mcgill.ca/triples/Barr-Wells-ctcs.pdf) Category Theory for Computing Science - Michael Barr and Charles Wells [CTCS-1st](http://fef.ogu.edu.tr/matbil/eilgaz/kategori.pdf)
-   Categories, Types, and Structures: An Introduction to Category Theory for the Working Computer Scientist [pdf](http://www.cs.unibo.it/~asperti/PAPERS/book.pdf)
-   Topoi, The Categorical Analysis of Logic, Robert Goldblatt [Amazon](http://www.amazon.com/Topoi-Categorial-Analysis-Logic-Mathematics/dp/0486450260)
-   [TTT](http://www.tac.mta.ca/tac/reprints/articles/12/tr12abs.html) - Toposes, Triples and Theories - Michael Barr and Charles Wells
-   Category Theory Lectures Notes for ESSLLI - Michael Barr and Charles Wells [pdf](http://www.math.upatras.gr/~cdrossos/Docs/B-W-LectureNotes.pdf)
-   [Seven Sketches in Compositionality: An Invitation to Applied Category Theory](https://arxiv.org/abs/1803.05316) - Brendan Fong, David I Spivak
-   [Applied Category Theory Course](http://www.azimuthproject.org/azimuth/show/Applied+Category+Theory+Course) - online course conducted by John Baez [forum](https://forum.azimuthproject.org/discussion/1717/welcome-to-the-applied-category-theory-course)
-   [CTFP](https://www.blurb.com/b/9008339-category-theory-for-programmers) - Category Theory for Programmers - [Bartosz Milewski](https://github.com/BartoszMilewski), created by [Igal Tabachnik](https://github.com/hmemcpy) from [series of blog posts](https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/); video lectures based on this material: [part 1](https://www.youtube.com/watch?v=I8LbkfSSR58&list=PLbgaMIhjbmEnaH_LTkxLI7FMa2HsnawM_), [part 2](https://www.youtube.com/watch?v=3XTQSx1A3x8&list=PLbgaMIhjbmElia1eCEZNvsVscFef9m0dm), [part 3](https://www.youtube.com/watch?v=F5uEpKwHqdk&list=PLbgaMIhjbmEn64WVX4B08B4h2rOtueWIL); [pdf](https://github.com/hmemcpy/milewski-ctfp-pdf)

#### Journals

-   [TAC](http://www.tac.mta.ca/tac/) - Theory and Applications of Categories

#### Subtopics

-   [Recursion Schemes](https://steshaw.org/plt/category-theory/recursion-schemes.html)

### Mathematics

Some related maths resources.

#### Mathematical Literacy/Thinking

It can be useful to have some background in mathematical thinking.

-   [Introduction to Mathematical Thinking](http://www.amazon.com/Introduction-Mathematical-Thinking-Keith-Devlin-ebook/dp/B009LTPSTO) — [Keith Devlin](http://profkeithdevlin.org/)
-   [How to prove it](http://www.amazon.com/How-Prove-It-Structured-Approach/dp/0521675995) — Daniel J. Velleman

#### Algebra

-   [A Computational Introduction to Number Theory and Algebra](http://shoup.net/ntb/) — Victor Shoup
-   Advanced Modern Algebra — Joseph J. Rotman [pdf](http://www.math.hcmuns.edu.vn/~nvdong/DaiSoDaiCuong/Advanced%20Modern%20Algebra%20-%20Joseph%20J.%20Rotman.pdf)
-   A Survey of Modern Algebra — Birkhoff and MacLane [Scribd](https://www.scribd.com/doc/127988704/Birkhoff-a-Survey-of-Modern-Algebra)

### Other collections

-   [Great Works in Programming Languages](http://www.cis.upenn.edu/~bcpierce/courses/670Fall04/GreatWorksInPL.shtml) — Benjamin Piece
-   [Classic Papers in Programming Languages and Logic](http://www.cs.cmu.edu/~crary/819-f09/) — Karl Crary
-   [The collected works of Per Martin-Löf](https://github.com/michaelt/martin-lof) — Michael Thompson and others
-   [PLT Texts Online](https://web.archive.org/web/20141002195305/http://www.cs.uu.nl:80/wiki/Techno/ProgrammingLanguageTheoryTextsOnline) — Frank Atanassow
-   [Functional programming books overview](http://alexott.net/en/fp/books/) — Alex (Alexey) Ott
-   [TypeFunc](https://github.com/williamdemeo/TypeFunc) — William Demeo
-   [Lambda the Ultimate](http://lambda-the-ultimate.org/) — Ehud Lamm et al.
-   [Archives of Lambda the Ultimate](http://www.angelfire.com/tx4/cus/lambda.html) (stale but includes “classic”) — Chris Rathman
-   [Programming Language People](http://www.angelfire.com/tx4/cus/people/index.html) — Chris Rathman
-   [PL Summer Schools forall](https://gist.github.com/biboudis/377b4a4de4d1718df2d0) — [Aggelos Biboudis](http://biboudis.github.io/)
-   [Summer Schools Interesting Conferences](http://user.it.uu.se/~bengt/Info/summer-schools.shtml) — [Bengt Jonsson](http://user.it.uu.se/~bengt/)
-   [The Programming Language Zoo](http://andrej.com/plzoo/) — [Andrej Bauer](http://math.andrej.com/)

We. Sell. UseCases.



> The Interface IS the Product

#### Certification is useless
Donald P. Hoyt, “The Relationship Between College Grades and Adult
Achievement.” Project Management Certification does not correlate with
performance:  
http://network.projectmanagers.net/profiles/blog/show?id=1606472%3ABlogPost%3A244660

#### Motivated teams:

Daniel Pink. Drive: The amazing truth about what motivates us. New York:
Riverhead Books, 2011.

#### Happiness Metric.

[https://sites.google.com/a/scrumplop.org/published-patterns/retrospective-pattern-language/happiness-metric](https://sites.google.com/a/scrumplop.org/published-patterns/retrospective-pattern-language/happiness-metric)

Hirotaka Takeuchi and Ikujiro Nonaka. The New New Product Development
Game. Harvard Business Review.
[https://hbr.org/1986/01/the-new-new-product-development-game](https://hbr.org/1986/01/the-new-new-product-development-game)

Jeff Sutherland. Origins of Scrum.
[https://www.scruminc.com/origins-of-scrum/](https://www.scruminc.com/origins-of-scrum/)

Bell Labs research Brendan G. Cain and James O. Coplien.

#### A Role-Based Empirical Process Modeling Environment.

In Proceedings of Second International Conference on the Software
Process (ICSP-2), pages 125-133, February 1993. Los Alamitos,
California, IEEE Computer Press.

Neil B. Harrison and James O. Coplien. Patterns of productive software
organizations. Bell Labs Technical Journal, 1(1):138- 145, Summer
(September) 1996.

#### Organizational Patterns of Agile Software

Development. Upper Saddle River, NJ: Prentice- Hall/Pearson, July 2004.
James Coplien and Neil Harrison.

#### SIMULA 67 Common Base Language. Norwegian

Computing Center, 1968. O.-J. Dahl, B. Myhrhaug, K. Nygaard:

#### Borland Software Craftsmanship: A New Look at Process,

Quality and Productivity. In Proceedings of the Fifth Borland
International Conference, Orlando, Florida, June 1994. James O. Coplien.

#### Agile Software Development with Scrum. Pearson,

October, 2001. Mike Beedle and Ken Schwaber.

#### Software in 30 Days: How Agile Managers Beat the Odds, Delight

Their Customers, and Leave Competitors in the Dust. Wiley, 2012. Ken
Schwaber.

Ikujiro Nonaka. The Knowledge Creating Company. Oxford University
Press, 1995.

Ikujiro Nonaka and R. Toyama. Managing Flow: A Process Theory of the
Knowledge-Based Firm. Palgrave Macmillan, 2008.

#### A Development Process Generative Pattern Language. In James O.

Coplien and Douglas C. Schmidt, editors, Pattern Languages of Program
Design, chapter 13, 183-237. Addison-Wesley, Reading, MA, 1995. James O.
Coplien.

#### A Laboratory for Teaching Object-Oriented Thinking. Proceedings of

OOPSLA ’89, SIGPLAN Notices 24(10), October, 1989. Kent Beck.

#### Architecture and the Child Within. Games versus Play,

gamification considered harmful, etc. James Coplien.
[https://www.slideshare.net/Avisi_ASAS/keynote-asas-2014-jim-coplien-the-child-within](https://www.slideshare.net/Avisi_ASAS/keynote-asas-2014-jim-coplien-the-child-within)

#### Objects as mental models.

Alan C. Kay. A Personal Computer for Children of All Ages. Original
between 1968 and 1982. New York: ACM Press, Proceedings of the ACM
Annual Conference - Volume 1, 1972,
http://doi.acm.org/10.1145/800193.1971922.

#### The Humane Interface: New Directions for Designing Interactive

Systems. Addison-Wesley: 2000. Jef Raskin.

#### A Laboratory for Teaching Object-Oriented Thinking. Proceedings of

OOPSLA ’89, SIGPLAN Notices 24(10), October, 1989. Kent Beck.

#### Comparative Case Study on the Effect of Test-Driven

Development on Program Design and Test Coverage, ESEM 2007 Siniaalto and
Abrahamsson,

#### Does Test-Driven Development Improve the Program Code? Alarming results from a Comparative Case Study.

Siniaalto and Abrahamsson, Proceedings of Cee-Set 2007, 10 - 12 October,
2007, Poznan, Poland.

On unit testing: Why Most Unit Testing is Waste.
https://rbcs-us.com/documents/Why-Most-Unit-Testing-is-Waste.pdf

#### Segue.

[https://rbcs-us.com/documents/Segue.pdf](https://rbcs-us.com/documents/Segue.pdf)

#### Toyota automation:

https://qz.com/196200/toyota-is-becoming-more-efficient-by-replacing-robots-with-humans/,

https://www.fastcompany.com/40461624/how-toyota-is-putting-humans-first-in-an-era-of-increasing-automation

#### Research on DCI by Héctor Valdecantos.

Héctor Valdecantos, Katy Tarrit, Mehdi Mirakhorli , and James O.
Coplien. An Empirical

#### Study on Code Comprehension: Data Context Interaction Compared to Classical Object Oriented.

Proceedings of ICPC 2017, IEEE Press, May 2017.

#### Long deliberation.

Jeffrey K. Liker. The Toyota Way. McGraw-Hill, 2004, Chapter 19.

#### Last Responsible Moment. Glenn Ballard. Positive versus negative iteration in

design. In Proceedings of the 8th Annual Conference on the International
Group for Lean Construction (IGLC-8). 2000, June.

#### The Quality without a Name. Christopher Alexander. The Timeless Way of Building.

Oxford University Press, 1979.

#### Mob Programming.

[https://en.wikipedia.org/wiki/Mob_programming](https://en.wikipedia.org/wiki/Mob_programming)

#### Organizational Learning. Joop Swieringa and Andre Wierdsma. Becoming a Learning

#### Organization: Beyond the Learning Curve. Addison-Wesley, 1992.

#### Stable Teams:

https://sites.google.com/a/scrumplop.org/published-patterns/product-organization-pattern-language/development-team/stable-teams

#### The Ten Bulls.

[https://sites.google.com/a/scrumplop.org/published-patterns/book-outline/preface ](https://sites.google.com/a/scrumplop.org/published-patterns/book-outline/preface)

#### The Design Movement:

John Thackara. Design After Modernism: Beyond the Object. New York:
Thames and Hudson, Inc., 1988. Nigel Cross, ed. Developments in design
methodology. Chichester, UK: Wiley, 1984.

Jeff Sutherland. The Scrum Handbook.
[https://www.researchgate.net/publication/301685699_Jeff_Sutherland%27s_Scrum_Handbook](https://www.researchgate.net/publication/301685699_Jeff_Sutherland%27s_Scrum_Handbook)

Daniel Pink. Drive: The amazing truth about what motivates us. New York:
Riverhead Books, 2011.

Differential comparison of two compilers, or of a compiler with its own
output when optimizations are turned off, usually requires a much more
restricted form of the program, which limits the bugs you find, since
programs must be compiled and executed to compare results.
[reference from trailofbits, https://blog.trailofbits.com/2021/03/23/a-year-in-the-life-of-a-compiler-fuzzing-campaign/](https://blog.trailofbits.com/2021/03/23/a-year-in-the-life-of-a-compiler-fuzzing-campaign/)

- [Differential Testing For Software](https://www.cs.swarthmore.edu/~bylvisa1/cs97/f13/Papers/DifferentialTestingForSoftware.pdf)


## About the efficient reduction of lambda terms

[Andrea Asperti](https://arxiv.org/search/cs?searchtype=author&query=Asperti%2C+A)

https://arxiv.org/pdf/1701.04240

## The optimal implementation of functional programming languages

-   January 1998

-   Publisher: Cambridge University Press
-   ISBN: 0 521 62112 7
