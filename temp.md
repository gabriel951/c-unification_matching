# Authors 
Mauricio Ayala-Rincón (1)  
Maribel Fernández (2)  
Ana Cristina Rocha-Oliveira (1)  
Gabriel Ferreira Silva (1)  
Daniele Nantes Sobrinho (1)  

(1) - Universidade de Brasília, (2) - King's College London   

# PVS Formalisation
##  Description  
In the directory "c-unification\_matching" you will find the .pvs and .prf files of the formalisation
of nominal c-unification with protected variables.  
The top subtheory is >> nominalEunif.pvs <<

The theory Nominal Unification consists of eight pvs files.

This was specified in PVS 6.0 (available at http://pvs.csl.sri.com) over
Mac OS and Linux platforms. Also, you will need the PVS NASA libraries
(available at http://shemesh.larc.nasa.gov/fm/ftp/larc/PVS-library). 
Running PVS opens an Emacs window. 

Uncompress and copy the nominal c-unification directory somewhere in your 
system. Then run PVS using as context library (change context) that 
directory.  

To follow a proof you should place the cursor over the lemma or theorem
you want to check and use the PVS meta commands `x-step-proof` (step by
step) or `x-prove`.
 
## Hierarchy 
The hierarchy of this theory is given as below, where "V" means that the 
theory above imports the theory below:

                        nominalEunif
                             |
                             V
                        substitution
                             |
                             V
                      alpha_equivalence
                             |
                             V
                         freshness
                             |
                             V
                        nominal_term
                         /    |     \
                        |     |      |
                        V     |      V
                     atoms    |    terms
                        |     |   
                        V     V   
                       structure_extra



## Files 
**atoms.pvs -** implementation of atoms as natural numbers, permutations 
          and the difference set (ds).

**nominal\_term.pvs -** contains the data structure of terms and auxiliary functions that
                 that deal with terms. Type checking will generate the additional 
                 pvs file: 

**term\_adt.pvs - ** contains all inductive proof schematta for this ADT.

**fresh.pvs -** contains the definition of freshness through the boolean recursive 
          function ``fresh" which checks if an atom is fresh for a term with 
          respect to a specific context. The function ``fresh?" does something 
          similar by verifying if an atom is fresh for a term in some context 
          and, simultaneously, it builds such a context, if it exists. Some 
          properties can be reached very easily, like that freshness is closed 
          over permutation action.

**alpha\_equivalence.pvs -** concerns alpha-equivalence, that is defined recursively 
          as the function ``alpha". The function alpha tests if two terms are 
          alpha-equivalent in a specific context. It is proved that alpha is 
          an equivalence relation. 

**substitution.pvs -** deals with substitutions (acting over variables only) and some 
          basic properties. There is a function named "fresh\_subs?" which apply 
          a substitution to a freshness context in the sense that, for each pair 
          (atom x variable) in the original context, it verifies if the atom is 
          fresh in the term obtained by applying the substitution to the 
          variable. This verification and the building of a proper new context 
          is made recursively by the function "fresh?". The function "fresh_subs?" 
          is used in the unification algorithm in order to update freshness 
          contexts. There are a number of auxiliary lemmas that are used in the
          formalization of the algorithm that were specified in this file. 

**nominalEunif.pvs -** It is 
          provided an algorithm through the function "c\_unify" to test if two 
          terms are unifiable and generate a correct and complete set of solutions. 
          Termination, soundness and completeness of this algorithm are already proved.

**structure\_extra.pvs -** includes auxiliary lemmas related with properties of 
          lists, non straightforwardly related with the nominal unification
          theory.

# Python Code
The Python code contains the files unify.py, example\_generator.py and tests.py: 

**unify.py -** contains the Python manual algorithm 

**example\_generator.py -** contains the code to generate random examples and the
experiments made

**tests.py -** contains preliminar tests to test if the algorithm was running as
intended 

