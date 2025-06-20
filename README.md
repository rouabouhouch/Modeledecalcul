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

![image](https://github.com/user-attachments/assets/86f8dbf9-fdb8-4828-aa65-92b35687d05c)
![image](https://github.com/user-attachments/assets/e08b2556-b187-460a-9e24-0a63ff7dc1b3)
![image](https://github.com/user-attachments/assets/ee6396e6-b338-4b2f-b6c6-321bb3119d02)

### Question 3
Question 3. Montrer que ((S K) K) se comporte comme I (et donc que I n’est pas necessaire).



Pour démontrer que `((S K) K)` se comporte comme `I`, nous devons montrer que pour tout argument `x`, l'application de `((S K) K)` à `x` produit le même résultat que l'application de `I` à `x`.

Nous utiliserons les définitions des combinateurs fournies dans les sources :

* **I** (Identité) : `(I x) → x`.
* **K** (Première projection) : `((K x) y) → x`.
* **S** (Application) : `(((S x) y) z) → ((x z) (y z))`.

---

### Réduction de `((S K) K) x` :

1. **Terme initial :**
   `((S K) K) x`
   Identifions ce terme avec la forme `(((S A) B) C)`, où :

   * `A = K`
   * `B = K`
   * `C = x`

   Appliquons la règle de réduction du combinateur **S** :
   `(((S A) B) C) → ((A C) (B C))`

   Donc :
   `((S K) K) x → ((K x) (K x))`

2. **Réduction de `((K x) (K x))` :**
   `(K x)` est une fonction qui prend un argument et retourne toujours `x`, ignorant cet argument.
   Appliquons la règle :
   `((K A) B) → A`

   Ici, `A = x` et `B = (K x)`. Donc :
   `((K x) (K x)) → x`

3. **Conclusion :**
   Puisque `((S K) K) x → x` pour tout `x`, le terme `((S K) K)` se comporte comme le combinateur identité `I`.

---

**Ainsi, le combinateur `I` peut être construit à partir de `S` et `K`, ce qui montre qu'il n'est pas strictement nécessaire.**




