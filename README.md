### Expressions du λ-calcul pur (syntaxique) :

Une **expression λ** $E$ est définie inductivement par :
| **Type d’Expression** | **Forme Syntaxique** | **Description**                            | **Exemple**         |
| --------------------- | -------------------- | ------------------------------------------ | ------------------- |
| **Variable**          | $x$                  | Une variable simple                        | $x$                 |
| **Abstraction**       | $\lambda x . E$      | Fonction anonyme avec paramètre $x$        | $\lambda x . x$     |
| **Application**       | $(E_1 \; E_2)$       | Application de la fonction $E_1$ sur $E_2$ | $(\lambda x . x) y$ |
---

### Notes complémentaires :

* Les parenthèses clarifient l’ordre mais peuvent être omises selon conventions.
* $E$, $E_1$, $E_2$ sont des expressions λ (recursif).
* Pas de types ni constantes, juste variables, abstractions, applications.

Voici ton texte réécrit au propre, clair et formel :

---
### Exercice 1 controle 2020
---

### Formes normales du λ-calcul pur

Montrer que toute expression \(N\) en forme normale est soit :

- une variable,  
- ou de la forme  
  \[
  \lambda x_1 \cdots \lambda x_n . (\cdots ((y E_1) E_2) \cdots E_m)
  \]
  avec \(y\) une variable et tous les \(E_i\) en forme normale.

---

### Rappels :

- Une expression est en forme normale si elle ne contient aucun rédexe β, c’est-à-dire aucune sous-expression de la forme \((\lambda x . M) N\).
- Les λ-termes sont construits inductivement :
  - Variable : \(x\)
  - Application : \((M N)\)
  - Abstraction : \(\lambda x . M\)

---

### Preuve par induction sur \(N\) :

**Cas 1 :** \(N\) est une variable.  
Alors \(N = x\) est forcément en forme normale.

---

**Cas 2 :** \(N = (M_1 M_2)\) est une application en forme normale.  
- \(M_1\) **ne peut pas** être une abstraction \(\lambda x . P\) (sinon \(N\) serait un rédexe β).  
- \(M_1\) et \(M_2\) sont en forme normale.  
- On peut donc écrire \(N\) sous forme gauche-associative :  
  \[
  (\cdots ((y E_1) E_2) \cdots E_m)
  \]
  où \(y\) est une variable (la tête à gauche) et les \(E_i\) sont en forme normale.

---

**Cas 3 :** \(N = \lambda x . M\) est une abstraction en forme normale.  
- \(M\) est en forme normale.  
- Par hypothèse d’induction, \(M\) est soit une variable, soit une application gauche-associative :  
  \[
  (\cdots ((y E_1) E_2) \cdots E_m)
  \]
- Si \(M\) est une abstraction, on "sort" les abstractions successives :  
  \[
  \lambda x \lambda y . M'
  \]
- Finalement,  
  \[
  N = \lambda x_1 \cdots \lambda x_n . T
  \]
  avec \(T\) non-abstraction en forme normale.

---

### Conclusion

Toute expression \(N\) en forme normale est soit :

- une variable,  
- ou une abstraction  
  \[
  \lambda x_1 \cdots \lambda x_n . (\cdots ((y E_1) E_2) \cdots E_m)
  \]
  avec \(y\) variable et \(E_i\) en forme normale.

---



# λ-calcul et combinateurs

On considère le système de combinateurs `S`, `K`, `I` défini comme suit :

- `I` est le combinateur identité :  
  `(I x) → x`

- `K` est le combinateur de première projection :  
  `((K x) y) → x`

- `S` est le combinateur d’application :  
  `(((S x) y) z) → ((x z) (y z))`

L’ensemble des termes de combinateurs est défini inductivement par :  
- une variable est un terme combinateur,  
- un combinateur “primitif” (`S`, `K` ou `I`) est un terme combinateur,  
- une application notée `(T1 T2)` de deux termes de combinateurs `T1` et `T2` est un terme combinateur.

---

### Question 2

Donner des λ-termes se comportant comme `S`, `K`, `I` (c’est-à-dire donnant les mêmes résultats sur les mêmes paramètres).


