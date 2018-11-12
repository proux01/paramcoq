Paramcoq
========

[![Build Status](https://travis-ci.com/coq-community/paramcoq.svg?branch=v8.7)](https://travis-ci.com/coq-community/paramcoq)

The plugin is still in an experimental state. 
It is not very user friendly (lack of good error messages) and still contains bugs. 
But is useable enough to "translate" a large chunck of standard library. 

Compilation 
-----------

The plugin is believed to work with Coq ≥ 8.7.
One way to test the plugin is to follow the following steps:

* Retrieve the plugin and compile it:

        git clone ...
        cd paramcoq 
        git checkout v8.x  # checkout branch according to Coq version
        make
        make install

* To test the plugin:

        cd test-suite
        make ide

    It will compile Parametricity.vo which loads the plugin. 
    Then, it launches CoqIDE with some simple examples. 

Available commands
------------------

The default arity is 2. 

- Parametricity *ident* as *name* [arity *n*].

Declare the translation named *name* from the translation of the constant or inductive *ident*.

- Parametricity [Recursive] *ident* [arity *n*] [qualified].

The default name for the translation of the constant or inductive *ident* is automatically generated (from its unqualified name).  
You can use the `Recursive` option to recursively translate all the constants and inductives which are used by *ident*.  
You can use the `qualified` option to use a qualified default name for the translated constants and inductives. The default name then has the form `Module_o_Submodule_o_ident` if *ident* lies in the `Module.Submodule` namespace.

- Parametricity Translation *term* [as *name*] [arity *n*]. 

Define a new constant named *name* obtained by computing the parametricity translation of *term*. 

- Parametricity Module *modulepath*.

Recursively translate everything in a module. 

- Realizer *constant or variable* [as *name*] [arity *n*] := *term*.

Declare *term* to be the translation of a constant. 
Useful to translate terms containing section variables, or axioms. 

Note that both translating a term or module may lead to proof obligations (for some fixpoints and opaque terms if you did not import `ProofIrrelevence`).

- [Global | Local] Parametricity Tactic := t.

Use the tactic t to solve proof obligations generated by the `Parametricity` command.

Contributors
------------

Original authors:
- [Chantal Keller](https://www.lri.fr/~keller/),
- [Marc Lasson](https://mlasson.github.io/).

External contributors (many thanks !):
- [Abhishek Anand](http://www.cs.cornell.edu/~aa755/),
- [Damien Rouhling](http://perso.ens-lyon.fr/damien.rouhling/).

License
-------

This software is distributed under the terms of the MIT License. See the
file `LICENSE` for details.
