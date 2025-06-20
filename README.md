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

---
### Exercice 1 controle 2020
---
![image](https://github.com/user-attachments/assets/c116c9a6-bb17-44fc-8014-ef7541a564e0)

![image](https://github.com/user-attachments/assets/852ec189-8ded-4e67-b0d3-7be997fa9064)
![image](https://github.com/user-attachments/assets/f05739b5-631d-4fab-80d1-2aab9bfb6e99)
![image](https://github.com/user-attachments/assets/b243a9e1-342d-4212-9f36-487d0bc485db)
![image](https://github.com/user-attachments/assets/c75ed716-b763-4c1c-ae73-455363cc5e26)
![image](https://github.com/user-attachments/assets/fda6ab38-8124-42dc-931c-97bff145ec28)
![image](https://github.com/user-attachments/assets/70f73d6f-1ca0-425b-9b49-2528f409bf1b)







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

Pour répondre à votre question, nous allons donner les λ-termes qui se comportent comme les combinateurs S, K, et I, en nous basant sur leurs définitions fournies.

Voici les λ-termes équivalents pour chaque combinateur :

- **Combinateur I (Identité)**  
  - Définition : `(I x)` se réduit en `x`.  
  - **λ-terme équivalent :**  
    \[
    \lambda x . x
    \]  
  - Explication : Ce λ-terme prend un argument \(x\) et retourne \(x\) lui-même, ce qui correspond exactement au comportement du combinateur identité.

- **Combinateur K (Première projection)**  
  - Définition : `((K x) y)` se réduit en `x`.  
  - **λ-terme équivalent :**  
    \[
    \lambda x . \lambda y . x
    \]  
  - Explication : Ce λ-terme prend un premier argument \(x\), puis un second argument \(y\), et retourne \(x\), ignorant \(y\). Cela modélise parfaitement la projection sur le premier élément.

- **Combinateur S (Application)**  
  - Définition : `(((S x) y) z)` se réduit en `((x z) (y z))`.  
  - **λ-terme équivalent :**  
    \[
    \lambda x . \lambda y . \lambda z . ((x z) (y z))
    \]  
  - Explication : Ce λ-terme prend trois arguments successivement : \(x\), \(y\), et \(z\). Il applique ensuite \(x\) à \(z\), et \(y\) à \(z\), puis applique le résultat de \((x z)\) au résultat de \((y z)\). C’est le comportement exact du combinateur S.


