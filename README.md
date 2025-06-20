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

**Pour prouver que toute expression** $N$ **du λ-calcul pur en forme normale (sans calcul possible) est soit une variable, soit de la forme**

$$
\lambda x_1 \cdots \lambda x_n. ( \cdots ((y\, E_1) E_2) \cdots E_m )
$$

avec les $E_i$ en forme normale et $y$ une variable,
nous procédons par **induction structurelle** sur $N$.

---

### Définitions préalables :

* Une expression est en **forme normale** si elle ne contient aucun rédexe β, c’est-à-dire aucune sous-expression de la forme $(\lambda x. E_1) E_2$, et ne peut donc plus être β-réduite.
* Les λ-termes sont définis inductivement par :

  * Toute variable $x$ est un λ-terme.
  * Si $E_1$ et $E_2$ sont des λ-termes, alors $(E_1 E_2)$ est une **application**.
  * Si $E$ est un λ-terme et $x$ une variable, alors $\lambda x. E$ est une **abstraction**.

---

### Preuve par induction structurelle sur $N$ :

**Cas 1 : $N$ est une variable**
Si $N = x$, alors $N$ ne contient aucun rédexe β, il est en forme normale.
Cela correspond directement à la première forme désirée.

---

**Cas 2 : $N$ est une application $(E_1 E_2)$**
Si $N = (E_1 E_2)$ est en forme normale, alors :

* $E_1$ **ne peut pas** être une abstraction $\lambda x. E'$, sinon $N$ serait un rédexe β, donc réductible.
* $E_1$ et $E_2$ doivent tous deux être en forme normale (sinon $N$ pourrait se réduire par réduction dans $E_1$ ou $E_2$).

Puisque $E_1$ n’est pas une abstraction, elle est soit une variable, soit une application.

* Si $E_1$ est une variable $y$, alors

$$
N = (y E_2)
$$

avec $E_2$ en forme normale, ce qui correspond à la forme demandée avec $m=1$.

* Si $E_1 = (F G)$ est une application en forme normale, on peut décomposer récursivement $F$ jusqu’à atteindre une variable $y$, ce qui donne une forme associée à gauche :

$$
N = (\cdots ((y E_1) E_2) \cdots E_m)
$$

avec tous les $E_i$ en forme normale.

---

**Cas 3 : $N$ est une abstraction $\lambda x. E$**
Si $N = \lambda x. E$ est en forme normale, alors :

* $E$ est en forme normale (sinon $N$ pourrait se réduire).
* On applique l’hypothèse d’induction à $E$ :

  * Soit $E$ est une variable $y$, alors

  $$
  N = \lambda x. y
  $$

  ce qui est une abstraction avec $n=1$ et $m=0$.

  * Soit $E$ est une application de la forme

  $$
  (\cdots ((y E'_1) E'_2) \cdots E'_m)
  $$

  avec tous les $E'_i$ en forme normale.
  Alors

  $$
  N = \lambda x. (\cdots ((y E'_1) E'_2) \cdots E'_m)
  $$
* Si $E$ est elle-même une abstraction $\lambda y. E''$, on répète le processus et on obtient finalement une forme

$$
\lambda x_1 \cdots \lambda x_n. T
$$

où $T$ n’est pas une abstraction et est en forme normale, ce qui revient à un cas précédent.

---

### Conclusion :

Toute expression $N$ en forme normale est soit :

1. Une variable,
2. Ou bien une abstraction

$$
\lambda x_1 \cdots \lambda x_n. (\cdots ((y E_1) E_2) \cdots E_m)
$$

avec $y$ une variable et les $E_i$ en forme normale.

---

**Cette conclusion correspond précisément à ce que l’on voulait démontrer.**

Voici une version bien formatée et claire de ton texte :

---

# λ-calcul et combinateurs

On considère le système de combinateurs $S, K, I$ défini comme suit :

* $I$ est le combinateur identité :

  $$
  (I \; x) \to x,
  $$

* $K$ est le combinateur de première projection :

  $$
  ((K \; x) \; y) \to x,
  $$

* $S$ est le combinateur d’application :

  $$
  (((S \; x) \; y) \; z) \to ((x \; z) \; (y \; z)).
  $$

L’ensemble des termes de combinateurs est défini inductivement par :

* une variable est un terme combinateur,
* un combinateur “primitif” ($S$, $K$ ou $I$) est un terme combinateur,
* une application notée $(T_1 \; T_2)$ de deux termes de combinateurs $T_1$ et $T_2$ est un terme combinateur.

---

### Question 2

Donner des $\lambda$-termes se comportant comme $S$, $K$, $I$ (c’est-à-dire donnant les mêmes résultats sur les mêmes paramètres).

---

