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
---
### Question 6

Justifier de la décidabilité ou non du problème ayant pour données :  
— Un terme combinatoire \( C_1 \),  
et pour question :  
— \( C_1 \) admet-il une forme normale, c’est-à-dire une forme irréductible par les 3 règles données en début de section 2 ?

---

Le problème de déterminer si un terme combinatoire \( C_1 \) admet une forme normale, c'est-à-dire une forme irréductible par les règles de réduction des combinateurs \( S, K, I \), est **non-décidable**.

Voici la justification, basée sur les informations de nos sources :

- **Équivalence des modèles de calcul** :  
  Les fonctions calculables par machine de Turing sont équivalentes aux fonctions récursives partielles et aux fonctions \(\lambda\)-représentables. Ainsi, le \(\lambda\)-calcul pur, et par extension le système de combinateurs \( S, K, I \) (qui peut représenter n'importe quel \(\lambda\)-terme), ont la même puissance de calcul que les Machines de Turing.

- **Problème de l'arrêt** :  
  Le problème de l'arrêt, qui consiste à déterminer si une machine de Turing s'arrête sur une entrée donnée, est **non-décidable**.

- **Lien entre forme normale et arrêt** :  
  Dans le contexte du \(\lambda\)-calcul (et donc des combinateurs), l'existence d'une forme normale pour un terme est directement équivalente à la terminaison du calcul (arrêt de la machine). Un terme est en forme normale s'il ne peut plus être réduit. Si un terme admet une forme normale, cela signifie que sa réduction se termine.


---

**En résumé**, déterminer si un terme combinatoire \( C_1 \) admet une forme normale est un problème **indécidable** en général.


| **Catégorie**              | **Problème**                         | **Définition claire**                                                                                                   | **Pourquoi cette catégorie ?**                                                                                           |
|---------------------------|------------------------------------|-------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| **Décidables**             | Langage récursif                   | Langage dont une Machine de Turing s’arrête toujours (acceptant ou rejetant) pour toute entrée.                          | Une MT existe qui finit toujours et dit "oui" ou "non" sans tourner à l’infini.                                           |
|                           | α-conversion (λ-calcul pur)        | Décider si deux λ-termes sont équivalents par renommage de variables liées.                                               | Algorithme existe pour comparer et dire si c’est vrai ou faux.                                                           |
|                           | Typabilité simple (λ-calcul typé)  | Décider si un λ-terme a un type selon les règles simples de typage.                                                      | Algorithme existe et finit toujours, car les règles sont syntaxiques et finies.                                           |
|                           | Calcul dans système T (Gödel)      | Toutes fonctions définies sont totales, c’est-à-dire toujours terminent.                                                 | Le système impose une structure qui garantit la terminaison des calculs.                                                 |
| **Semi-décidables**        | Problème de l’arrêt (acceptation)  | Déterminer si une MT accepte une entrée donnée (peut tourner indéfiniment sinon).                                         | Si oui, MT finit par accepter (donc semi-décidable). Sinon, elle peut tourner à l’infini, impossible à détecter.           |
|                           | Langage récursivement énumérable   | Langage pour lequel une MT liste toutes les chaînes acceptées (mais peut tourner à l’infini sur les non-membres).         | MT énumère les mots, donc semi-décidable, mais pas forcément décidable.                                                  |
| **Co-Semi-décidables**     | Complément d’un langage r.é.        | Langage dont le complément est récursivement énumérable.                                                                 | Si tu peux semi-décider que quelque chose n’est *pas* dans le langage, alors il est co-semi-décidable.                     |
| **Non décidable**          | Problème de l'arrêt total           | Savoir si une MT s'arrête sur *toutes* les entrées possibles.                                                            | Non décidable car ça généralise le problème de l’arrêt simple et aucun algorithme ne peut toujours trancher.               |
|                           | Problème de vacuité                 | Savoir si le langage reconnu par une MT est vide (n’accepte aucun mot).                                                   | Impossible à décider car il faudrait tester toutes les entrées possibles, ce qui est infini.                               |
|                           | Égalité de langages r.é.            | Savoir si deux MT reconnaissent le même langage.                                                                           | Indécidable car comparer deux langages infinis reconnus par MT est équivalent à un problème d’arrêt compliqué.            |
|                           | Égalité de fonctions calculables   | Savoir si deux fonctions calculées par MT donnent les mêmes résultats pour toutes les entrées.                           | Indécidable, car cela nécessite vérifier un comportement infini sur toutes les entrées.                                   |
|                           | Existence d’une forme normale \( C_1 \) | Savoir si un terme combinatoire admet une forme normale (arrêt des réductions).                                           | Indécidable car équivalent à savoir si une réduction λ-calcul (ou machine de Turing) termine.                             |
|                           | Relation de β-conversion (=β)       | Savoir si deux λ-termes sont équivalents par réduction β.                                                                  | Indécidable, reflétant la complexité extrême du λ-calcul pur.                                                             |
| **NP**                    | EXACT COVER BY 3-SETS               | Trouver une sélection de triplets qui couvre exactement un ensemble donné sans chevauchement.                            | Solution candidate vérifiable en temps polynomial, mais trouver la solution est dur.                                     |
|                           | SET PACKING                        | Trouver un sous-ensemble d’ensembles disjoints maximal.                                                                    | Facile à vérifier si un sous-ensemble est valide, mais dur à construire.                                                  |
|                           | CIRCUIT LE PLUS LONG                | Trouver un chemin simple le plus long dans un graphe orienté.                                                             | Vérifier un chemin donné est facile, trouver le plus long est dur.                                                       |
|                           | ENSEMBLE INDÉPENDANT               | Trouver un ensemble de sommets sans arêtes entre eux dans un graphe.                                                      | Vérifier est simple, trouver l’ensemble maximal est dur.                                                                 |
| **NP-Complets**            | TRIPARTITE MATCHING                | Trouver un couplage parfait dans un graphe triparti.                                                                      | Problème classique NP-complet, dur même à vérifier efficacement.                                                         |
|                           | CLIQUE                            | Trouver un sous-graphe complet de taille \(k\) dans un graphe.                                                             | Vérifier clique est simple, trouver la plus grande est NP-complet.                                                       |
|                           | 3-SAT et 3-SAT-NAE                | Décider si une formule booléenne en forme normale conjonctive (3 littéraux par clause) est satisfiable.                   | Problème canonique NP-complet, clé en complexité.                                                                         |
|                           | CIRCUIT HAMILTONIEN               | Trouver un cycle passant une fois par tous les sommets dans un graphe.                                                    | Vérifier un cycle est simple, trouver le cycle est NP-complet.                                                           |
|                           | Problème du circuit le plus long  | Trouver un chemin le plus long (pas nécessairement simple) dans un graphe.                                                | NP-complet par réduction depuis circuit hamiltonien.                                                                      |



| **Catégorie**                      | **Concept**                          | **Définition / Propriété**                                             | **Exemple / Info Clé**                                        |
| ---------------------------------- | ------------------------------------ | ---------------------------------------------------------------------- | ------------------------------------------------------------- |
| 🔧 Machines de Turing              | Machine de Turing                    | Modèle avec bande infinie, tête lecture/écriture, règles de transition | Simule tout programme : lire/écrire/bouger/changer état       |
|                                    | Composants                           | M = (V, B, Q, q0, F, T)                                                | T(q,a) = (b, dir, q′) → écrire b, déplacer tête, changer état |
|                                    | Configuration                        | Instantané : contenu bande + position tête + état                      | (w1, q, w2)                                                   |
|                                    | Exécution                            | Passage config → config via T                                          | Si T(q,a) défini, exécution possible                          |
|                                    | MT déterministe                      | Une règle possible par (état, symbole)                                 | Un seul chemin d’exécution                                    |
|                                    | MT non déterministe                  | Plusieurs transitions possibles                                        | Exploration en arbre                                          |
| 🧪 Langages & calculabilité        | Langage reconnu                      | Ensemble des mots menant à un état final                               | "1010" reconnu si mène à qf                                   |
|                                    | Langage récursif (décidable)         | MT s’arrête toujours, accepte si mot ∈ L                               | Ex : vérifier parité                                          |
|                                    | Langage réc. énumérable (r.é.)       | MT s’arrête si mot ∈ L, sinon boucle ou rejette                        | Problème de l’arrêt                                           |
|                                    | Langage co-réc. énumérable (co-r.é.) | Le complément est r.é. → MT s’arrête si mot ∉ L                        | Ex : problème de vacuité                                      |
|                                    | Fonction Turing-calculable           | MT qui calcule f(x) si elle s’arrête sur x                             | f(x) = x+1                                                    |
|                                    | Thèse de Church-Turing               | Toute fonction calculable par procédure effective l’est par une MT     | MT ≡ λ-calcul ≡ fonctions récursives                          |
|                                    | MT Universelle                       | MT qui simule toute autre MT                                           | Interpréteur universel                                        |
| 💥 Problèmes classiques            | Problème de l’arrêt                  | Savoir si M s’arrête sur w ?                                           | Semi-décidable ✅, décidable ❌, co-semi-décidable ❌            |
|                                    | Problème de la vacuité               | Est-ce que L(M) = ∅ ?                                                  | Indécidable ❌, co-semi-décidable ✅, semi-décidable ❌          |
|                                    | Non-vacuité                          | L(M) ≠ ∅ ?                                                             | Semi-décidable ✅                                              |
|                                    | Égalité de langages r.é.             | L(M1) = L(M2) ?                                                        | Ni semi-décidable ni co-semi-décidable ❌                      |
|                                    | Égalité de fonctions Turing-calc.    | ∀x, f(x) = g(x) ?                                                      | Indécidable, même niveau                                      |
|                                    | Arrêt uniforme                       | M s’arrête sur toutes les entrées ?                                    | Non r.é., non co-r.é.                                         |
| 🧠 Définitions logiques            | Décidable                            | MT s’arrête toujours, accepte ssi w ∈ L                                | Langage récursif                                              |
|                                    | Semi-décidable                       | MT s’arrête si w ∈ L, sinon boucle ou rejette                          | Langage réc. énumérable                                       |
|                                    | Co-semi-décidable                    | MT s’arrête si w ∉ L, sinon boucle ou rejette                          | Complément est semi-décidable                                 |
|                                    | L récursif ⇔ L et ¬L r.é.            | Si L et son complément sont semi-décidables ⇒ L est décidable          | Base pour construire des preuves                              |
| 🔧 Réductions                      | Réduction (décidabilité)             | L1 ↝ L2 et L2 décidable ⇒ L1 décidable                                 | Propagation d’algorithme                                      |
|                                    | Réduction (indécidabilité)          | L1 indécidable et L1 ↝ L2 ⇒ L2 indécidable                             | Propagation de l’impossibilité                                |
| 🧱 Théorème de Rice                | Propriétés non triviales             | Toute propriété non triviale de langages r.é. est indécidable          | Ex : vacuité, finitude, égalité                               |
| 🧩 Classe NP                      | NP                                   | Problèmes dont solution vérifiable en temps polynomial                 | Sudoku, SAT                                                   |
|                                    | NP-complet                           | Plus durs de NP. Résoudre un = résoudre tous                           | SAT est NP-complet                                            |
|                                    | Réduction polynomiale                | Transformer problème en un autre rapidement                            | SAT → 3SAT → Clique                                           |
|                                    | Problèmes NP                         | Tous les problèmes NP sont décidables                                  | Complexes mais calculables                                    |
| 🛠 Variantes équivalentes          | Alphabet binaire uniquement          | Codage de l’alphabet V sur k bits (0/1)                                | Simulation possible                                           |
|                                    | Sans transitions sur place           | Simulées via droite puis gauche                                        | Nécessite états intermédiaires                                |
|                                    | MT à plusieurs bandes                | k bandes simulées sur une seule via encodage                           | Plus lent mais équivalent                                     |
|                                    | MT à plusieurs têtes                 | Têtes et positions simulées sur une bande                              | Plus complexe mais possible                                   |
|                                    | MT à deux piles                      | p1 = gauche de tête, p2 = droite                                       | Simulation parfaite possible                                  |
|                                    | Problème arrêt 2 piles               | Même indécidabilité que MT classique                                   | Problème de l’arrêt                                           |
| 📚 Clôtures                        | Récursifs (décidables)               | Fermés sous ∪, ∩, ¬                                                    | Très stables algorithmiquement                                |
|                                    | Récursivement énumérables            | Fermés sous ∪, ∩, **pas** ¬                                            | L_u r.é. mais ¬L_u non r.é.                                   |
|                                    | Clôture et décidabilité              | L et ¬L semi-décidables ⇒ L est récursif                               | Technique de preuve                                           |

Pour montrer qu’un problème \( P_2 \) est **NP-complet**, il faut faire deux choses :

1. **Montrer que \( P_2 \) est dans NP**  
   Cela veut dire qu’on peut vérifier rapidement (en temps polynomial) si une solution proposée à \( P_2 \) est correcte.

2. **Montrer que \( P_1 \) (problème déjà connu NP-complet) se réduit à \( P_2 \) en temps polynomial**  
   Cela signifie qu’on peut transformer n’importe quelle instance de \( P_1 \) en une instance de \( P_2 \) rapidement, et que la solution existe dans \( P_1 \) si et seulement si elle existe dans \( P_2 \).

Si ces deux conditions sont remplies, alors \( P_2 \) est NP-complet.

En gros, \( P_2 \) est au moins aussi dur que \( P_1 \), et ses solutions se vérifient vite.

Exemples :  
- *EXACT COVER BY 3-SETS* est NP-complet grâce à une réduction depuis *TRIPARTITE MATCHING*.  
- *ENSEMBLE INDÉPENDANT* est NP-complet via une réduction depuis *CLIQUE*.
