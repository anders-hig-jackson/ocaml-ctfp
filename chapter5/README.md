# Products and Coproducts
* Universal Construction
  - Defining objects in terms of their relationships.
* Initial Object
  - The object that has one and only arrow to any object in the category.
  - This object is unique upto isomorphism.
* Absurd definition
```ocaml
# type void
```
```ocaml
# let rec absurd (x:void) = absurd x
```
* Terminal Object
  - One and only morphism coming to it from any object in the category.
  - Unique upto isomorphism.
```ocaml
# let unit x = ()
```
```ocaml
# let yes _ = true
```
```ocaml
# let no _ = false
```
* For any Category C, we can reverse the arrows and define opposite category.
* Constructions in the opposite category are prefixed with "co".
## Isomorphisms
* Propositional equality, intensional equality, extensional equality and equality as a path in homotopy type theory.
* Isomorphism is an even weaker notion of equivalence.
* Isomorphism - Object that look the same and have an one to one mapping between them(Invertible morphism)
```ocaml
# let compose f g x = f (g x)
# let id x = x
```
* Pseudo Ocaml for expression function equality
```ocaml
compose f g = id
```
* Initial and Terminal objects are *unique upto unique isomorphism*.
* This uniqueness upto unique isomorphism is the basis for all universal construction.
## Products
```ocaml
# let fst (a,b) = a
```
```ocaml
# let snd (a, b) = b
```
```ocaml
# let fst (a,_) = a
# let snd (_, b) = b
```
* Object *c* and two morphisms *p* and *q* connecting it to *a* and *b*
```ocaml
module type Chapter5_Product_ = sig
  type a
  type c
  type b
  val p : c -> a
  val q : c -> b
end
```
* Example with *Int* and *Bool*
```ocaml
module Chapter5_Product_Example: Chapter5_Product with type a = int and type b = bool and type c = int = struct
  type a = int
  type b = bool
  type c = int
  let p (x:int) = x
  let q (_:int) = true
end
```
* Example with *c* as (int, int, bool)
```ocaml
module Chapter5_Product_Example2: Chapter5_Product = struct
  type a = int
  type b = bool
  type c = int * int * bool
  let p (x,_,_) = x
  let q (_,_,b) = b
end
```