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

Ok, je vois que le problème vient surtout de la mise en forme LaTeX qui a un peu foiré dans ton texte copié-collé. Je te réécris ça **au propre**, bien formaté en Markdown + LaTeX, avec les bonnes virgules et parenthèses — prêt à être copié direct sans souci :

---

# Correction claire et rigoureuse

**Problème :** Montrer que toute expression $N$ en forme normale du λ-calcul pur est soit :

* une variable,
* ou bien de la forme

  $$
  \lambda x_1 \cdots \lambda x_n. \big( \cdots ((y \, E_1) E_2) \cdots E_m \big)
  $$

  avec $y$ une variable, et tous les $E_i$ en forme normale.

---

## Rappels importants

* Une expression est en **forme normale** si elle ne contient aucun rédexe β, c’est-à-dire aucune sous-expression réductible de la forme $(\lambda x. M) N$.
* Les termes du λ-calcul sont construits inductivement par :

  * Variables : $x$
  * Applications : $(M N)$
  * Abstractions : $\lambda x. M$

---

## Démonstration par induction structurelle sur $N$ :

### 1. Cas où $N$ est une variable

* Une variable $x$ ne contient pas de rédexe.
* Elle est donc forcément en forme normale.
* C’est la première forme possible.

---

### 2. Cas où $N = (M_1 M_2)$ est une application

* $N$ est en forme normale, donc **pas de rédexe possible**.
* Donc, $M_1$ **ne peut pas** être une abstraction $\lambda x. P$, sinon

  $$
  N = (\lambda x. P) M_2
  $$

  serait un rédexe β, donc réductible — ce qui contredit que $N$ est en forme normale.
* Donc $M_1$ est soit une variable, soit une application (mais pas une abstraction).
* De plus, $M_1$ et $M_2$ doivent tous deux être en forme normale, sinon $N$ pourrait être réduit via une réduction interne dans $M_1$ ou $M_2$.

---

**On peut donc décomposer $N$ comme une application gauche-associative de la forme :**

$$
(\cdots ((y \, E_1) E_2) \cdots E_m)
$$

* où $y$ est une variable (car $M_1$ n’est pas abstraction, on remonte à la variable la plus à gauche),
* et tous les $E_i$ sont en forme normale.

---

### 3. Cas où $N = \lambda x. M$ est une abstraction

* $N$ est en forme normale donc $M$ est en forme normale (sinon réduction possible à l’intérieur de $M$).
* On applique l’hypothèse d’induction à $M$.

**Selon l’hypothèse :**

* $M$ est soit une variable, soit une application gauche-associative de la forme

  $$
  (\cdots ((y \, E_1) E_2) \cdots E_m)
  $$

  avec $y$ une variable et tous les $E_i$ en forme normale.

* Si $M$ est aussi une abstraction, on la “sort” en la mettant devant $\lambda x$, on écrit alors :

  $$
  \lambda x \lambda y. M'
  $$

  ce qui rentre dans la forme souhaitée avec plusieurs abstractions consécutives.

---

## Conclusion finale

Toute expression $N$ en forme normale est soit :

* Une variable,
* Ou bien une abstraction

  $$
  \lambda x_1 \cdots \lambda x_n. (\cdots ((y \, E_1) E_2) \cdots E_m)
  $$

  où $y$ est une variable et tous les $E_i$ sont en forme normale.

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


