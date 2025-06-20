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

---
Question 4.

On rappelle qu’une **variable libre** dans un terme est une variable qui apparaît non liée par un λ dans ce terme.

On peut écrire un terme combinateur de comportement équivalent à n’importe quel λ-terme.

Pour convertir un λ-terme en une application de combinateurs ayant le même comportement, on utilise l’interprétation φ suivante :

1. φ(x) = x
2. φ((E₁ E₂)) = (φ(E₁) φ(E₂))
3. (a) φ(λx.E) = (K φ(E)) si x **n’est pas libre** dans E, sinon :

   (b) φ(λx.x) = I

   (c) φ(λx.λy.E) = φ(λx.φ(λy.E)) (si x est libre dans E)

   (d) φ(λx.(E₁ E₂)) = ((S φ(λx.E₁)) φ(λx.E₂)) (si x est libre dans E₁ ou dans E₂)

---

**Exercice :**

Donner un terme combinateur de comportement équivalent à `λx.λy.(y x)`.

---




Pour convertir le λ-terme `λx.λy.(y x)` en un terme combinateur équivalent, on applique récursivement les règles d’interprétation φ :

---

**1.** On commence par

$$
φ(λx.λy.(y x))
$$

Le terme est de la forme $λx.E$ avec $E = λy.(y x)$.
$x$ est libre dans $E$ (puisque $x$ apparaît dans $(y x)$).
Comme $E$ est une abstraction, on utilise la règle (c) :

$$
φ(λx.λy.(y x)) = φ(λx.(φ(λy.(y x))))
$$

---

**2.** On calcule maintenant

$$
φ(λy.(y x))
$$

Ici, $y$ est libre dans $(y x)$ et c’est une application $(E_1 E_2)$ avec $E_1 = y$, $E_2 = x$.
On applique la règle (d) :

$$
φ(λy.(y x)) = (S φ(λy.y)) (φ(λy.x))
$$

* $φ(λy.y) = I$ (règle (b))
* $φ(λy.x) = K x$ (règle (a), car $y$ n’est pas libre dans $x$)

Donc :

$$
φ(λy.(y x)) = (S I) (K x)
$$

---

**3.** On revient à

$$
φ(λx.((S I) (K x)))
$$

$x$ est libre dans $(K x)$, c’est une application $(A B)$ avec $A = (S I)$, $B = (K x)$.
On applique la règle (d) :

$$
φ(λx.((S I) (K x))) = (S φ(λx.(S I))) (φ(λx.(K x)))
$$

* Pour $φ(λx.(S I))$, $x$ n’est pas libre dans $(S I)$, donc par (a) :

$$
φ(λx.(S I)) = K (S I)
$$

* Pour $φ(λx.(K x))$, c’est une application $(K x)$ avec $x$ libre dans $x$, donc on applique (d) :

$$
φ(λx.(K x)) = (S φ(λx.K)) (φ(λx.x))
$$

* $φ(λx.K) = K K$ (car $x$ pas libre dans $K$)
* $φ(λx.x) = I$

Donc :

$$
φ(λx.(K x)) = (S (K K)) I
$$

---

**4.** **Résultat final :**

$$
φ(λx.λy.(y x)) = (S (K (S I))) ((S (K K)) I)
$$

---

Ce terme combinateur se comporte donc exactement comme `λx.λy.(y x)`.



---
## Question 3

Voici la version formatée clairement et structurée :

---

**Vérification que le terme combinateur**
`((S (K (S I))) ((S (K K)) I))`
**se comporte comme**
`λx.λy.(y x)`

---

Nous allons appliquer ce terme combinateur à deux arguments arbitraires, notés `a` et `b`, et montrer qu'il se réduit à `(b a)`.

---

### Rappels des règles de réduction des combinateurs :

* `(I x) → x` (Identité)
* `((K x) y) → x` (Première projection)
* `(((S x) y) z) → ((x z) (y z))` (Application)

---

### Soit le terme

`C = ((S (K (S I))) ((S (K K)) I))`
Nous évaluons :
`C a b`

---

### Étape 1 : Application de `S` externe

`((S (K (S I))) ((S (K K)) I)) a`
est de la forme `(((S X) Y) Z)` où :

* `X = (K (S I))`
* `Y = ((S (K K)) I)`
* `Z = a`

Par la règle de `S` :
`(((S X) Y) Z) → ((X Z) (Y Z))`

Donc :
`((S (K (S I))) ((S (K K)) I)) a → ((K (S I)) a) (((S (K K)) I) a)`

---

### Étape 2 : Réduction de `((K (S I)) a)`

De la forme `((K P) Q)` avec :

* `P = (S I)`
* `Q = a`

Par la règle de `K` :
`((K P) Q) → P`

Donc :
`((K (S I)) a) → (S I)`

---

### Étape 3 : Réduction de `(((S (K K)) I) a)`

De la forme `(((S X') Y') Z')` où :

* `X' = (K K)`
* `Y' = I`
* `Z' = a`

Par la règle de `S` :
`(((S X') Y') Z') → ((X' Z') (Y' Z'))`

Donc :
`(((S (K K)) I) a) → ((K K) a) (I a)`

---

### Étape 4 : Réduction des sous-termes

* `((K K) a)` :
  Forme `((K P'') Q'')` avec `P''=K` et `Q''=a`
  Par la règle de `K` :
  `((K K) a) → K`

* `(I a)` :
  Forme `(I P''')` avec `P'''=a`
  Par la règle de `I` :
  `(I a) → a`

En remplaçant :
`((K K) a) (I a) → (K a)`

---

### Étape 5 : Assemblage et application de `b`

Le résultat partiel de l’étape 1 est :
`(S I) (K a)`

On applique maintenant `b` :
`((S I) (K a)) b`

De la forme `(((S X''') Y''') Z''')` où :

* `X''' = I`
* `Y''' = (K a)`
* `Z''' = b`

Par la règle de `S` :
`(((S X''') Y''') Z''') → ((X''' Z''') (Y''' Z'''))`

Donc :
`((S I) (K a)) b → (I b) ((K a) b)`

---

### Étape 6 : Réduction finale

* `(I b)` :
  `(I b) → b`

* `((K a) b)` :
  `((K a) b) → a`

En remplaçant :
`(I b) ((K a) b) → (b a)`

---

### Conclusion

Nous avons montré que :
`((S (K (S I))) ((S (K K)) I)) a b → (b a)`

Or,
`(λx.λy.(y x)) a b → (b a)`

Donc, le terme combinateur `((S (K (S I))) ((S (K K)) I))` se comporte **exactement** comme le λ-terme `λx.λy.(y x)`.

