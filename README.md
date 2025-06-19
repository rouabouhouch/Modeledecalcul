

### 🧠 Tableau Synthèse Ultime – Machines de Turing, Classes de Langages, Problèmes, Variantes, Clôtures **(ENRICHIE)**

| **Catégorie**               | **Concept**                          | **Définition / Propriété**                                                                                      | **Exemple / Info Clé**                                                            |
| --------------------------- | ------------------------------------ | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| 🔧 Machines de Turing       | Machine de Turing                    | Modèle formel pour la notion d’algorithme. Utilise une bande infinie, une tête, un alphabet et des états.       | Simule tout programme : lire/écrire/bouger/changer état                           |
|                             | Composants                           | M = (V, B, Q, q0, F, T) avec V = alphabet d’entrée, B = bande, Q = états, q0 = état init, F = finaux, T = trans | T(q,a) = (b, dir, q′) → lire `a`, écrire `b`, déplacer tête (←/→), aller à q′     |
|                             | Configuration                        | Instantané de l’exécution : ce qui est écrit, où est la tête, et l’état actuel                                  | Représenté par un triplet (w1, q, w2) où la tête est sur le 1er symbole de w2     |
|                             | Exécution                            | Application successive des règles de transition à une configuration donnée                                      | S’arrête si aucune règle applicable ou si atteint un état final                   |
|                             | MT déterministe                      | Une seule règle par (état, symbole) : pas de choix possible                                                     | Exécution unique → + simple à analyser                                            |
|                             | MT non déterministe                  | Plusieurs transitions possibles → l’exécution explore un arbre                                                  | Peut simuler via MT déterministe avec exploration exhaustive (mais + lent)        |
| 🧪 Langages & calculabilité | Langage reconnu                      | Un mot est reconnu si la MT atteint un état final pour ce mot                                                   | Ne garantit pas arrêt pour les mots non reconnus                                  |
|                             | Langage récursif (décidable)         | MT s’arrête **toujours**, accepte ssi mot ∈ L                                                                   | On peut répondre **oui ou non** en temps fini                                     |
|                             | Langage réc. énumérable (r.é.)       | MT s’arrête **seulement** si mot ∈ L (accepte), sinon elle peut tourner à l’infini                              | ⛔ Rejeter = pas garanti → semi-décidabilité                                       |
|                             | Langage co-réc. énumérable (co-r.é.) | Complément est r.é. = on reconnaît **les mots non dans L**                                                      | Pareil, pas garanti de répondre oui, mais on peut dire non en s’arrêtant          |
|                             | Fonction Turing-calculable           | Si MT s’arrête sur **chaque entrée** x, elle calcule f(x)                                                       | Ex : f(x) = x+1 ou f(x) = somme de chiffres                                       |
|                             | Thèse de Church-Turing               | Toute fonction "effectivement calculable" peut l’être par une MT                                                | Equivalence MT ↔ λ-calcul ↔ fonctions récursives                                  |
|                             | MT Universelle                       | MT U qui prend une MT M et une entrée w et simule M sur w                                                       | Comme un interpréteur Python qui lit un programme Python                          |
| 💥 Problèmes classiques     | Problème de l’arrêt                  | Est-ce que M s’arrête sur w ?                                                                                   | Indécidable ❌, mais **semi-décidable** ✅ : on peut détecter si **elle s’arrête**  |
|                             | Problème de la vacuité               | Est-ce que L(M) = ∅ ?                                                                                           | ❌ Indécidable, ✅ co-semi-décidable : on peut détecter les cas **non vides**       |
|                             | Non-vacuité                          | L(M) ≠ ∅ ?                                                                                                      | ✅ Semi-décidable : il suffit de trouver **un mot accepté**                        |
|                             | Égalité de langages r.é.             | L(M1) = L(M2) ?                                                                                                 | 🔥 Ni semi-décidable ni co-semi-décidable                                         |
|                             | Égalité de fonctions Turing-calc.    | ∀x, f(x) = g(x) ?                                                                                               | Même complexité que l’arrêt → indécidable                                         |
|                             | Arrêt uniforme                       | Est-ce que M s’arrête sur **toutes** les entrées ?                                                              | Ultra-chaud : même pas r.é. ni co-r.é.                                            |
| 🧠 Définitions logiques     | Décidable                            | MT **accepte ou rejette** chaque mot en **temps fini**                                                          | = Langage récursif                                                                |
|                             | Semi-décidable                       | MT s’arrête **seulement si** le mot est dans le langage                                                         | = Langage r.é.                                                                    |
|                             | Co-semi-décidable                    | MT s’arrête **seulement si** le mot n’est pas dans le langage                                                   | = Complément d’un r.é.                                                            |
|                             | L récursif ⇔ L et ¬L r.é.            | Si L et son complément sont tous deux semi-décidables → L est décidable                                         | Utilisé pour prouver la décidabilité                                              |
| 🔧 Réductions               | Réduction (décidabilité)             | Si L1 ↝ L2 et L2 est décidable, alors L1 aussi                                                                  | ⚠️ Faut une réductibilité efficace (ex : fonction calculable)                     |
|                             | Réduction (indécidabilité)           | Si L1 est indécidable et L1 ↝ L2, alors L2 l’est aussi                                                          | Technique pour propager l’indécidabilité                                          |
| 🧱 Théorème de Rice         | Propriétés non triviales             | Toute propriété non triviale d’un langage reconnu par une MT est indécidable                                    | Non trivial = vraie pour au moins un langage et fausse pour au moins un autre     |
| 🧩 Classe NP                | NP                                   | Problèmes dont **une solution** peut être vérifiée en temps polynomial par une machine déterministe             | ⛔ Trouver solution = dur, ✅ Vérifier solution = facile                            |
|                             | NP-complet                           | Problèmes les + "compliqués" de NP : tout problème NP peut s’y réduire                                          | Si t’en résous un en poly → tu résous tous les autres                             |
|                             | Réduction polynomiale                | Transformer un problème en un autre en **temps polynomial**                                                     | SAT → 3SAT → CLIQUE → plein d'autres                                              |
|                             | Problèmes NP                         | Tous sont **décidables**, même si résolution peut être exponentielle                                            | Classe ⊆ P^?^ (si P = NP ? 😵‍💫)                                                 |
| 🛠 Variantes équivalentes   | Alphabet binaire uniquement          | Toute MT avec alphabet ≠ binaire peut être **encodée** sur binaire                                              | Simule par codage (ex: a → 00, b → 01, etc.)                                      |
|                             | Sans transitions sur place           | Peut être simulé en écrivant puis revenant                                                                      | Nécessite des états intermédiaires                                                |
|                             | MT à plusieurs bandes                | k bandes peuvent être encodées sur une seule bande avec séparateurs                                             | Rend la MT + rapide (dans les faits), mais pas + puissante                        |
|                             | MT à plusieurs têtes                 | Simulable avec une seule bande + codage de positions                                                            | Beaucoup + galère mais même puissance                                             |
|                             | MT à deux piles                      | Équivaut à MT classique                                                                                         | Peut simuler pile via la bande                                                    |
|                             | Problème arrêt 2 piles               | Toujours indécidable                                                                                            | Même complexité que MT classique                                                  |
| 📚 Clôtures                 | Récursifs (décidables)               | Fermés sous ∪, ∩, ¬, concaténation, étoile                                                                      | Super stables : tu peux construire des langages compliqués et garder décidabilité |
|                             | Récursivement énumérables            | Fermés sous ∪, ∩ mais **pas** ¬                                                                                 | Ex : L\_u = r.é., mais ¬L\_u = pas r.é. → pas fermé sous complément               |
|                             | Clôture et décidabilité              | Si L et ¬L sont tous deux semi-décidables ⇒ L est récursif                                                      | À mémoriser comme théorème de characterization                                    |

---

---

### 📚 **Clôtures – Définitions & Propriétés enrichies**

| **Concept**                                   | **Définition / Propriété**                                                                                                                                                                 | **Exemple / Info Clé**                                                                            |                   |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- | ----------------- |
| **Opération**                                 | Une opération transforme des langages en un autre : ∪, ∩, ¬, concaténation, étoile, homomorphisme, etc.                                                                                    | Exemple : L₁ ∪ L₂ = {w                                                                            | w ∈ L₁ ou w ∈ L₂} |
| **Clôture**                                   | Une **classe de langages** est dite **fermée** (ou **clôturée**) par une opération si appliquer cette opération à des langages de la classe donne un langage qui **reste dans la classe**. | Ex : Si L₁ et L₂ sont récursifs, alors L₁ ∩ L₂ est aussi récursif → donc récursif **fermé** par ∩ |                   |
| **Fermeture (mathématiquement)**              | Soit une classe **C**, et une opération **◦**, on dit que C est **fermée** par ◦ si ∀ L₁, L₂ ∈ C ⇒ L₁ ◦ L₂ ∈ C                                                                             | Formule clean : C est fermée par ◦ ⟺ ∀ L₁,L₂ ∈ C, L₁ ◦ L₂ ∈ C                                     |                   |
| **Utilité des clôtures**                      | Connaître les opérations de clôture permet de construire de nouveaux langages **sans sortir de la classe**, ou de **prouver qu’un langage n’y est pas** s’il n’est pas stable.             | Strat de preuve : si L₁ ∪ L₂ ∉ C alors l’un au moins des deux n’est pas dans C                    |                   |
| **Langages récursifs (≡ décidables)**         | **Fermés sous :** ∪, ∩, ¬, concaténation, étoile, etc.                                                                                                                                     | Super classe stable → combine tout, reste toujours décidable                                      |                   |
| **Langages récursivement énumérables (r.é.)** | **Fermés sous :** ∪, ∩ mais **pas** sous ¬ (complément)                                                                                                                                    | ⚠️ Le complément d’un r.é. n’est **pas forcément** r.é.                                           |                   |
| **Langages co-récursivement énumérables**     | Fermés sous ∪, mais pas forcément sous ∩ ni ¬                                                                                                                                              | Pareil, la fermeture est partielle                                                                |                   |
| **Clôture et intersection**                   | r.é. et co-r.é. sont **fermés sous intersection avec un récursif**                                                                                                                         | Si L ∈ r.é. et R ∈ récursif ⇒ L ∩ R ∈ r.é.                                                        |                   |
| **Non-fermeture utile en preuve**             | Si tu sais qu’une classe n’est **pas fermée** sous une opération, tu peux t’en servir pour montrer qu’un langage **n’appartient pas** à cette classe                                       | Ex : ¬L\_u n’est pas r.é. → donc r.é. n’est pas fermé sous complément                             |                   |
| **Test de double semi-décidabilité**          | Si L ∈ r.é. et ¬L ∈ r.é. ⇒ L est récursif                                                                                                                                                  | Méga classique en exam pour détecter si un langage est dans la classe des décidables              |                   |

---


### 🧠 Machine Universelle (Mu) – Synthèse **avec exemples concrets**

| **Aspect**                           | **Définition / Fonction**                                                                                                                                | **Exemple concret**                                                                                        |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| 🔍 **Définition**                    | Mu est une machine de Turing capable de **simuler** toute autre machine M sur une entrée `w`. Elle lit le code de M et exécute ses instructions sur `w`. | Comme un **interpréteur Python** qui lit un fichier `.py` et l’exécute ligne par ligne.                    |
| 🧾 **Entrée de Mu**                  | Un mot codé contenant la **description de la machine M** (⟨M⟩) + un **mot d’entrée** `w` pour cette machine.                                             | Exemple : `⟨M_pair⟩#1010`, où M\_pair teste si un binaire est pair.                                        |
| 💽 **Bandes utilisées (à 3 bandes)** | **B1** : contient `⟨M⟩#w` <br> **B2** : simule la bande de M <br> **B3** : stocke l’état courant de M                                                    | B1 : description complète d’un programme + son input. <br> B2 : comme la RAM d’un programme en cours.      |
| ⚙️ **Fonctionnement**                | Mu copie `w` sur B2, `q0` sur B3. Puis elle lit B1 pour chercher la règle `(état, symbole)` de M. Elle simule l’effet : écrit, bouge, change état.       | Si `⟨M⟩` dit "si tu lis 1 en état q0, écris 0 et va à q1", Mu le fait sur B2 et B3.                        |
| 🔄 **Simulation**                    | À chaque étape, Mu lit l’état (B3), le symbole lu (B2), trouve la règle (dans B1), puis applique la transition.                                          | C’est comme si tu suivais un tutoriel codé étape par étape pour exécuter manuellement un programme.        |
| 📥 **Programme = donnée**            | ⟨M⟩ n’est pas exécuté "en dur" mais **lu comme donnée**. Donc un programme peut être lu et exécuté par un autre.                                         | Tu peux stocker du code dans un fichier texte et le faire exécuter par Python = exactement ce que fait Mu. |

---

### 💥 Impacts concrets et implications de Mu

| **Conséquence**                                 | **Explication**                                                                                                           | **Exemple concret**                                                                                           |                                                                                                        |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| ✅ **Appartenance semi-décidable**               | Si tu veux savoir si une machine M accepte `w`, Mu peut le simuler. Si M accepte `w`, Mu finit par l’accepter aussi.      | Ex : `⟨M_pair⟩#1010` → Mu tourne et accepte car 1010 est pair.                                                |                                                                                                        |
| 🚫 **Pas de rejet certain**                     | Si `w` n’est pas accepté par M, Mu peut **tourner en boucle** sans jamais s’arrêter.                                      | Ex : `⟨M_pair⟩#111` (111 = impair), M tourne en boucle → Mu aussi. Pas de "non" garanti.                      |                                                                                                        |
| 🔥 **Problème de l’arrêt**                      | On ne peut pas savoir si M va **s’arrêter** ou **boucler** sur une entrée `w`.                                            | Ex : `⟨M_inf⟩#w`, où M\_inf est conçue pour boucler tout le temps : impossible de le détecter **à coup sûr**. |                                                                                                        |
| ❌ **Complément non calculable**                 | Le complément de \`Lu = {⟨M,w⟩                                                                                            | M accepte w}\` **n’est pas** récursivement énumérable.                                                        | Il n’existe pas de machine qui accepte ⟨M,w⟩ **seulement** quand M **rejette** w ou tourne à l’infini. |
| 🚧 **Limites claires de la calculabilité**      | Mu montre qu’il y a des choses que **même un super ordi infini** ne peut pas résoudre.                                    | Comme "ce programme va-t-il tourner pour toujours ?" → même Mu ne peut pas répondre.                          |                                                                                                        |
| 🔁 **Réduction = propagation d’indécidabilité** | En partant du problème de l’arrêt, on peut **prouver que d’autres problèmes sont aussi indécidables**.                    | Ex : savoir si `L(M) = ∅` → tu peux construire une MT M’ basée sur M et dire : si elle s’arrête, alors...     |                                                                                                        |
| 📚 **Théorème de Rice**                         | Toute propriété **non triviale** (pas toujours vraie ou fausse) sur les langages acceptés par une MT est **indécidable**. | "Est-ce que M accepte un langage fini ?" → pas décidable. "Est-ce que M accepte un palindrome ?" → pareil.    |                                                                                                        |

---

### 🎯 Résumé simple à retenir :

| 🧠 Ce qu’il faut retenir de Mu                                                     |
| ---------------------------------------------------------------------------------- |
| ✔ Mu = simulateur général de n’importe quelle machine de Turing                    |
| ✔ Elle **prouve que les programmes peuvent être traités comme des données**        |
| ✔ Grâce à elle, on **définit les langages récursivement énumérables**              |
| ❌ Elle ne permet pas de résoudre le **problème de l’arrêt**                        |
| ❌ Elle révèle l’**existence de limites** dans ce qui est calculable                |
| ✔ Elle est utilisée pour **réduire** des problèmes et **prouver l’indécidabilité** |

---



## 🧪 **EXEMPLE : Mu simule une machine M qui accepte seulement le mot `0`**

### 🎯 But :

La machine M accepte le mot `0`, et **rejette tout le reste**.
On veut que **Mu simule M sur deux entrées** :

* ✅ Cas 1 : `⟨M⟩#0` → M accepte `0`
* ❌ Cas 2 : `⟨M⟩#1` → M rejette `1` (en tournant en boucle ici, pour illustrer la semi-décidabilité)

---

## 🧰 Composants de la Machine Universelle (Mu)

| **Bande**   | **Contenu initial**                                | **Rôle**                                                |
| ----------- | -------------------------------------------------- | ------------------------------------------------------- |
| **Bande 1** | `⟨M⟩#w` (code de la machine + mot `w` à tester)    | Contient la **description de M** + **mot d'entrée `w`** |
| **Bande 2** | Vide au départ → contiendra le **mot `w`**         | Simule la **bande de M**                                |
| **Bande 3** | Vide au départ → contiendra **l’état courant** `q` | Suivre l’**état dans lequel se trouve M**               |

---

## ✅ **Cas 1 : Mu simule `⟨M⟩#0`**

| Étape | Bande 1 (⟨M⟩#0) | Bande 2 (bande simulée de M) | Bande 3 (état de M) | Explication                                                |
| ----- | --------------- | ---------------------------- | ------------------- | ---------------------------------------------------------- |
| 1     | `⟨M⟩#0`         | `0`                          | `q0`                | Mu copie `0` sur B2 et met `q0` sur B3                     |
| 2     | `⟨M⟩#0`         | `0`                          | `q0`                | Mu lit : dans `q0` sur symbole `0`, va à `qf` (état final) |
| 3     | `⟨M⟩#0`         | `0`                          | `qf`                | L'état final est atteint : **Mu accepte**                  |

🎉 Résultat : **Mu accepte** cette entrée → donc `0 ∈ L(M)`

---

## ❌ **Cas 2 : Mu simule `⟨M⟩#1`**

| Étape | Bande 1 (⟨M⟩#1) | Bande 2 (bande simulée de M) | Bande 3 (état de M) | Explication                                               |
| ----- | --------------- | ---------------------------- | ------------------- | --------------------------------------------------------- |
| 1     | `⟨M⟩#1`         | `1`                          | `q0`                | Mu copie `1` sur B2 et met `q0` sur B3                    |
| 2     | `⟨M⟩#1`         | `1`                          | `q0`                | Mu cherche une règle dans ⟨M⟩ pour `(q0,1)`...            |
| 3     | `⟨M⟩#1`         | `1`                          | `q0`                | ... il n’y en a pas. Alors soit Mu boucle, soit M boucle. |
| 4+    | `⟨M⟩#1`         | `1`                          | `q0`                | La machine **ne termine jamais**.                         |

😵 Résultat : **Mu ne s'arrête pas**, car M ne sait pas quoi faire → `1 ∉ L(M)`

---

## 🧠 Ce que tu vois ici :

| Situation | Mu s'arrête ? | Résultat                                      |
| --------- | ------------- | --------------------------------------------- |
| `⟨M⟩#0`   | Oui           | Mot accepté ✅                                 |
| `⟨M⟩#1`   | Non           | Pas accepté ❌ mais **pas de "non" explicite** |

💡 **Et c’est exactement pour ça que ce langage `Lu = {⟨M,w⟩ | M accepte w}` est semi-décidable et pas décidable** :
Tu peux savoir quand c’est **oui**, mais tu ne sauras jamais vraiment quand c’est **non**.

---

### 🧾 Énumérateur – Tableau synthèse avec exemples concrets

| **Catégorie**                     | **Concept**          | **Définition / Propriété**                                                                                 | **Exemple concret / Info Clé**                                        |                                                      |
| --------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ---------------------------------------------------- |
| 🔧 **Structure d’un énumérateur** | Bande de travail     | Bande standard pour effectuer les calculs                                                                  | Comme une MT normale                                                  |                                                      |
|                                   | Bande de sortie      | Tête ne va qu’à droite, **imprime les mots du langage** un par un                                          | Sortie en série : `w₁`, `w₂`, `w₃`, …                                 |                                                      |
|                                   | Ordre canonique      | Les mots peuvent être énumérés selon un **ordre logique** (ex: binaire croissant)                          | Ex : "", "0", "1", "00", "01", "10", "11", etc.                       |                                                      |
| 🧠 **Définition clé**             | Énumérateur          | MT qui **produit tous les mots d’un langage** L, sans entrée                                               | Il imprime en boucle tous les `w ∈ L`, un après l’autre               |                                                      |
|                                   | Équivalence          | **L est récursivement énumérable ⇔ L est énumérable**                                                      | Si L est r.é., alors il existe un énumérateur pour L                  |                                                      |
| ✅ **Sens direct**                 | r.é. ⇒ énumérable    | Une MT qui accepte L peut être modifiée pour **énumérer tous les mots** qu’elle accepte                    | On génère tous les mots possibles, et on les teste un par un          |                                                      |
| 🔁 **Sens réciproque**            | énumérable ⇒ r.é.    | Si un mot est imprimé par l’énumérateur, alors il appartient à L → on peut construire une MT qui accepte L | Pour reconnaître `w`, on attend qu’il sorte : s’il sort, on accepte   |                                                      |
| 📚 **Implications**               | Langage r.é.         | Les mots de L peuvent être **produits** (mais pas nécessairement testés ou rejetés)                        | Ex : \`Lu = {⟨M,w⟩                                                    | M accepte w}\` est r.é. mais pas récursif            |
|                                   | Langage non r.é.     | Si aucun énumérateur n’existe pour un langage, alors ce langage **n’est pas** récursivement énumérable     | Ex : \`¬Lu = {⟨M,w⟩                                                   | M n’accepte pas w}\` n’est **même pas** r.é.         |
| 🚫 **Décidabilité**               | Langage récursif     | S’il existe des **énumérateurs pour L et ¬L**, alors L est **décidable**                                   | On peut tester les deux en parallèle : le mot va sortir d’un des deux |                                                      |
|                                   | Langage non récursif | Si `L` est r.é. mais `¬L` ne l’est pas, alors **L n’est pas récursif**                                     | Typique des problèmes comme le **problème de l’arrêt**                |                                                      |
| 🔥 **Problème de l’arrêt**        | Lu = {⟨M, w⟩         | M accepte w}                                                                                               | Est r.é. (→ a un énumérateur), mais pas récursif                      | On peut énumérer les couples ⟨M,w⟩ où M accepte w    |
|                                   | ¬Lu = {⟨M, w⟩        | M n’accepte pas w}                                                                                         | N’est pas r.é. (→ aucun énumérateur possible)                         | Donc on **ne peut pas prouver** qu’un mot est rejeté |

---

### 🧠 Résumé express : ce qu’il faut graver dans ton cortex 🧠

| ✅ Rappels clés                                                                   |
| -------------------------------------------------------------------------------- |
| 🔹 Un langage est **r.é.** ↔ il existe un **énumérateur** qui le produit         |
| 🔹 L’énumérateur **sort** tous les mots du langage, dans un certain ordre        |
| 🔹 Il **ne prend pas de mot en entrée** : il **produit** les éléments du langage |
| 🔹 Le **problème de l’arrêt** est r.é. (donc énumérable) mais **non récursif**   |
| 🔹 Son complément n’est **même pas r.é.**, donc **non énumérable**               |

---


| **Catégorie**                         | **Concept**                               | **Définition / Propriété**                                                                                 | **Exemple / Info clé**                                                                             |
| ------------------------------------- | ----------------------------------------- | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **Problèmes**                         | Problème de décision                      | Question avec réponse "oui" ou "non" : est-ce que \$w \in L\$ ?                                            | Décider si un mot appartient à un langage donné                                                    |
|                                       | Décidable                                 | Machine de Turing s’arrête toujours, accepte si \$w \in L\$, rejette sinon                                 | Langage récursif                                                                                   |
|                                       | Semi-décidable (récursivement énumérable) | Machine de Turing s’arrête et accepte si \$w \in L\$, sinon peut boucler ou rejeter                        | Langage semi-décidable (exemple : problème de l’arrêt)                                             |
|                                       | Fonction Turing-calculable                | Fonction calculable par une Machine de Turing qui s’arrête pour toute entrée                               | Exemple : \$f(x) = x + 1\$                                                                         |
| **Complexité et NP**                  | NP                                        | Classe de problèmes où la solution peut être vérifiée en temps polynomial                                  | Sudoku, SAT                                                                                        |
|                                       | NP-Complétude                             | Problème dans NP auquel tous les autres problèmes NP peuvent se réduire en temps polynomial                | SAT est un problème NP-complet                                                                     |
|                                       | Réduction polynomiale                     | Transformation rapide (en temps polynomial) d’un problème \$P\_1\$ vers \$P\_2\$                           | Si \$P\_1 \leadsto P\_2\$ et \$P\_1\$ NP-complet alors \$P\_2\$ est NP-difficile                   |
|                                       | Méthode pour prouver NP-complétude        | 1) Montrer que \$P\_2\$ est dans NP ; 2) Réduire un problème NP-complet \$P\_1\$ à \$P\_2\$ rapidement     | Si OK, alors \$P\_2\$ est NP-complet                                                               |
| **Exemples de problèmes NP-Complets** | TRIPARTITE MATCHING (TM)                  | Trouver triplets disjoints couvrant trois ensembles \$B, G, H\$                                            | Problème NP-complet connu                                                                          |
|                                       | EXACT COVER BY 3-SETS (EC)                | Trouver \$m\$ ensembles de 3 éléments disjoints couvrant un ensemble \$U\$                                 | Réduction de TM à EC prouvant la NP-complétude de EC                                               |
|                                       | CIRCUIT HAMILTONIEN                       | Trouver un chemin passant une seule fois par tous les sommets                                              | Problème NP-complet classique                                                                      |
|                                       | CIRCUIT LE PLUS LONG                      | Trouver un circuit de longueur ≥ \$k\$ sans répétition de sommets                                          | NP-complet, réduit depuis CIRCUIT HAMILTONIEN                                                      |
|                                       | CLIQUE                                    | Trouver un sous-graphe complet de taille \$k\$                                                             | Problème NP-complet                                                                                |
|                                       | ENSEMBLE INDÉPENDANT                      | Trouver un ensemble de \$k\$ sommets sans arêtes entre eux                                                 | NP-complet, réduction depuis CLIQUE                                                                |
|                                       | SET PACKING                               | Trouver \$k\$ ensembles disjoints dans une famille d’ensembles                                             | NP-complet, réduction depuis EXACT COVER BY 3-SETS                                                 |
| **Réductions et implications**        | Réduction \$L\_1 \leadsto L\_2\$          | \$w \in L\_1\$ si et seulement si \$f(w) \in L\_2\$, avec \$f\$ calculable en temps polynomial             | Si \$L\_2\$ est récursif alors \$L\_1\$ l’est ; si \$L\_1\$ indécidable alors \$L\_2\$ l’est aussi |
|                                       | NP-complétude                             | Les problèmes les plus durs de NP : résoudre un seul NP-complet permet de résoudre tous les autres en poly | Point clé pour classer les problèmes                                                               |

---
Bien sûr, voici le tableau sans les symboles \$ pour que ce soit plus fluide et simple :

| **Étape**                                     | **Description**                                                                                          | **Exemple / Détail**                                                                                           |
| --------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **1. Vérifier que P2 est dans NP**            | Montrer qu'une solution candidate pour P2 peut être vérifiée en temps polynomial par une MT déterministe | Pour EXACT COVER (EC), vérifier qu’une proposition de couverture est correcte en temps polynomial              |
| **2. Réduire un problème P1 NP-Complet à P2** | Construire une transformation rapide (polynomiale) d’une instance w de P1 en une instance f(w) de P2     | Réduction de TRIPARTITE MATCHING (TM) à EXACT COVER (EC) : transformer les triplets en ensembles de 3 éléments |
| **Conclusion**                                | Si P2 est dans NP et P1 réduit à P2, alors P2 est NP-Complet                                             | EC est NP-Complet car TM est NP-Complet et réduit à EC                                                         |
| **Exemple 1 : TM → EC**                       | TM : triplets disjoints couvrant B, G, H (NP-Complet)                                                    | EC : trouver m ensembles disjoints de taille 3 couvrant un ensemble U de cardinal 3m                           |
| **Exemple 2 : CH → CLL**                      | CH (Circuit Hamiltonien) est NP-Complet                                                                  | CLL (Circuit le plus long) : montrer que CH est un cas particulier de CLL, donc réduction polynomiale possible |
| **Exemple 3 : CLIQUE → EI**                   | CLIQUE (sous-graphe complet) est NP-Complet                                                              | EI (Ensemble Indépendant) correspond à clique dans graphe complémentaire ; réduction polynomiale               |
| **Exemple 4 : EC → SP**                       | EC est NP-Complet                                                                                        | SP (Set Packing) : chercher k ensembles disjoints, réduction polynomiale à partir d’EC                         |

---

Bref, la recette pour prouver qu’un problème est NP-Complet, c’est :

1. montrer qu’il est dans NP, et
2. montrer que tu peux réduire un problème déjà NP-Complet en lui.

Ça garantit que le problème est aussi dur que les plus durs de NP.

### exemple:
---

| Étape                                        | Description détaillée                                                                                                                                                                                                                                                                                                   |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1. Définition du problème P₂**             | **CIRCUIT LE PLUS LONG (CLL)** :<br>- Données : un graphe G de n nœuds et un entier k.<br>- Question : existe-t-il un circuit dans G de longueur ≥ k, sans répéter un nœud ?                                                                                                                                            |
| **2. Montrer que P₂ est dans NP**            | On peut vérifier rapidement (en temps polynomial) qu’un circuit candidat :<br>- A une longueur ≥ k.<br>- Ne passe pas deux fois par le même nœud.<br>Donc CLL ∈ NP.                                                                                                                                                     |
| **3. Choix du problème P₁**                  | On prend comme P₁ le problème **CIRCUIT HAMILTONIEN (CH)**, qui est déjà prouvé NP-Complet :<br>chercher un circuit passant une fois par chaque nœud (longueur = n).                                                                                                                                                    |
| **4. Réduction polynomiale P₁ → P₂**         | Transformation simple et rapide (polynomiale) :<br>- Instance CH : graphe G.<br>- Instance CLL : même graphe G, et k = n (nombre de nœuds).                                                                                                                                                                             |
| **5. Preuve de la validité de la réduction** | - Si G a un circuit hamiltonien, alors il existe un circuit de longueur exactement n dans G → instance CLL (G, n) a réponse "oui".<br>- Si CLL (G, n) est "oui", alors il existe un circuit de longueur ≥ n dans G, donc forcément un circuit hamiltonien (car il ne peut pas y avoir plus de n nœuds sans répétition). |
| **6. Conclusion**                            | Puisque :<br>- P₂ = CLL est dans NP.<br>- P₁ = CH est NP-Complet et se réduit polynômialement à P₂.<br>Alors CLL est NP-Complet.                                                                                                                                                                                        |

---

### Pourquoi c’est important ?

* La vérification rapide d’une solution candidate (étape 2) signifie que CLL appartient à NP.
* La réduction polynomiale (étape 4-5) montre que si on pouvait résoudre CLL efficacement, on pourrait aussi résoudre CH efficacement.
* Comme CH est un problème "difficile" connu, CLL l’est aussi.
* Ce raisonnement est la base de la preuve de NP-Complétude : on se sert d’un problème dur déjà connu (CH) pour montrer qu’un nouveau problème (CLL) est au moins aussi dur.

---

### En résumé ultra-simple

* **CLL est facile à vérifier → CLL ∈ NP.**
* **CH ≤p CLL (réduction polynomiale).**
* **CH est NP-Complet.**
* Donc **CLL est NP-Complet.**

---


### Focus sur la **Réduction Polynomiale** et sa **Preuve de Validité**

**Contexte :**
On veut prouver que **CLL** (Circuit le Plus Long) est au moins aussi dur que **CH** (Circuit Hamiltonien), qui est déjà connu super dur (NP-Complet).

---

### C’est quoi une réduction polynomiale ?

C’est une **transformation efficace (rapide, en temps polynomial)** d’un problème qu’on connaît bien (ici CH) vers un autre (ici CLL) de façon à ce que :

* Si tu sais résoudre le problème cible (CLL), tu peux l’utiliser pour résoudre le problème source (CH).
* En gros, résoudre CLL = pouvoir résoudre CH, donc CLL est au moins aussi compliqué que CH.

---

### Dans notre exemple :

| Action                   | Exemple concret                                                                                                |
| ------------------------ | -------------------------------------------------------------------------------------------------------------- |
| **Problème source (CH)** | Trouver un circuit passant une fois par tous les nœuds du graphe G (longueur = n)                              |
| **Problème cible (CLL)** | Trouver un circuit de longueur au moins k dans le graphe G (sans repasser par un nœud)                         |
| **Réduction**            | Prends l’instance CH (graphe G) et transforme-la en instance CLL : même graphe G + k = nombre de nœuds (k = n) |

---

### Pourquoi cette réduction marche ? (preuve de validité)

1. **Si CH est "oui" (c’est-à-dire qu’il existe un circuit hamiltonien dans G), alors CLL est "oui" pour (G, n)**

   * Parce que ce circuit hamiltonien est un circuit de longueur exactement n (tous les nœuds).
   * Donc, dans CLL, on cherche un circuit de longueur ≥ n → ce circuit est pile ce qu’on cherche.

2. **Si CLL est "oui" pour (G, n), alors CH est "oui"**

   * Parce que si tu trouves un circuit de longueur ≥ n sans répéter de nœud, et que le graphe a exactement n nœuds, alors ce circuit doit forcément passer par **tous les nœuds une seule fois** (sinon impossible de faire plus long).
   * Donc ce circuit est un circuit hamiltonien.

---

### En résumé simple :

* Pour chaque instance du problème CH, on crée une instance équivalente du problème CLL en fixant k = nombre de nœuds.
* Résoudre CLL, c’est résoudre CH (au moins aussi dur).
* La transformation ne prend pas trop de temps (juste un simple passage du nombre de nœuds en paramètre).
* Donc, si on trouve un algorithme efficace pour CLL, on en aurait un pour CH — or on sait que CH est dur → CLL est aussi dur.

---

### Illustration imagée :

Imagine que tu cherches un chemin dans une ville avec 5 arrêts (n=5).

* CH : "Est-ce que je peux faire un tour qui passe une fois par chaque arrêt ?"
* CLL : "Est-ce que je peux faire un tour qui fait au moins k arrêts sans passer deux fois par le même ?"
  Si tu poses k=5, répondre "oui" à CLL, c’est répondre "oui" à CH.

---

### Fonction Rec
| **Thème**                                   | **Description Simplifiée**                                                                                                                              | **Exemples / Remarques**                                                                                        |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Contexte général**                        | Les fonctions récursives sont un modèle de calcul fondamental, équivalent aux machines de Turing et au λ-calcul.                                        | Fonctions définies à partir de fonctions simples et de schémas (composition, récursion, minimisation).          |
| **Fonctions récursives primitives (RP)**    | Fonctions construites par composition et récursion primitive, toujours totales (toujours définies).                                                     | Constantes, successeur (x+1), projections, addition, multiplication, prédécesseur, négation, etc.               |
| **Schéma de minimisation**                  | Permet de définir des fonctions partielles en cherchant le plus petit k tel que g(k, args) = 0, ce qui étend RP aux fonctions récursives générales (R). | Exemple : division entière par 2, racine carrée entière, fonctions qui peuvent ne pas s’arrêter (non totales).  |
| **Exemples précis de fonctions**            | Multiplication par 2, division entière par 2, reste modulo 2, prédécesseur, négation, conjonction logique, test d'égalité, soustraction tronquée, etc.  | Certaines sont primitives, d'autres utilisent la minimisation (donc pas primitives).                            |
| **Fonctions de manipulation de listes**     | Fonctions pour accéder aux éléments, inverser, compter la longueur, etc., définies par récursion et minimisation.                                       | nth, revnth, length (longueur), nthrm (k-ième reste), etc.                                                      |
| **Fonctions modélisant Machines de Turing** | Codage des configurations et règles de transition comme fonctions récursives, pour étudier la calculabilité des MT.                                     | Transition codée par des fonctions f1, f2, f3 sur la configuration.                                             |
| **Fonctions dans le λ-calcul**              | λ-calcul peut représenter les mêmes fonctions récursives (ADD, MULT, points fixes, somme de listes, etc.), montrant l'équivalence des modèles.          | Opérateur de point fixe, addition, multiplication, doubler, carré, somme des carrés dans une liste, longueur.   |
| **Équivalence des modèles**                 | Fonctions récursives = fonctions calculables par MT = fonctions exprimables en λ-calcul (Thèse de Church-Turing).                                       | Toutes les notions de calculabilité reposent sur cette équivalence.                                             |
| **Totalité et partialité**                  | RP : fonctions totales (toujours finies). R : fonctions récursives générales, peuvent être partielles (pas toujours définies).                          | Le système T de Gödel exprime plus que RP mais pas toutes les fonctions totales.                                |
| **Rôle en complexité**                      | Ces fonctions servent de base aux notions de temps polynomial et aux réductions entre problèmes, fondement des preuves de NP-Complétude.                | Opérations de base (add, mult) sont calculables en temps polynomial, ce qui rend les transformations efficaces. |

---


# Mini Cheat Sheet : Comment utiliser `Comp` pour construire des fonctions

| Étape | Action                                                                          | Exemple concret                                            | Explication rapide                                                 |
| ----- | ------------------------------------------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------------------ |
| 1     | Identifier les fonctions de base ou déjà définies                               | `add`, `minus`, `times2`, `div2`, `π_{k,i}` (projection)   | Ce sont tes blocs Lego déjà faits                                  |
| 2     | Pour créer une nouvelle fonction `h` qui utilise ces fonctions, tu écris        | `h = Comp(f, g_1, g_2, ..., g_n)`                          | `f` est la fonction principale, les `g_i` produisent ses arguments |
| 3     | Chaque `g_i` peut être soit une projection, soit une autre composition          | Par exemple `g_1 = π_{2,1}`, `g_2 = Comp(times2, π_{2,2})` | Tu peux imbriquer `Comp` autant que tu veux                        |
| 4     | La fonction finale s’écrit comme un arbre d’appels composés                     | Par exemple : `h(x,y) = add(x, times2(y))` devient         | `Comp(add, π_{2,1}, Comp(times2, π_{2,2}))`                        |
| 5     | Pour les fonctions récursives primitives, utilise aussi `Rec` pour la récursion | Exemple : prédécesseur `pred = Rec(C0, π_{1,1})`           | `Rec(b, h)` définit `f(0) = b` et `f(k+1) = h(k, f(k))`            |

---

# Schéma mental

```
              Comp
             /    \
            f      [g_1, g_2, ..., g_n]
                    /       |        \
            (proj1) (Comp)   (proj3) ...

Exemple : h(x,y) = add(x, times2(y))

              Comp (add)
             /           \
         π_{2,1}      Comp (times2)
                          |
                     π_{2,2}
```

* `Comp` : fonction principale + arguments transformés
* `π_{k,i}` : projection, récupère un argument
* Tu peux imbriquer `Comp` à volonté, toujours en respectant la structure.

---

# Exemple complet avec explication pas à pas

**Construisons** la fonction `mod2(x)` = reste de la division de `x` par 2.

On sait :

* `mod2(x) = x - times2(div2(x))`
* `times2(x) = add(x, x)` (déjà défini)
* `div2` est une fonction déjà définie

**Forme `Comp`** :

$$
mod2 = Comp(minus, \pi_{1,1}, Comp(times2, Comp(div2, \pi_{1,1})))
$$

**Décomposition :**

* Le premier argument de `minus` est `π_{1,1}` → récupère `x`.
* Le deuxième argument est `Comp(times2, Comp(div2, π_{1,1}))` → c’est la composition imbriquée qui fait :

  * Prend `x` via `π_{1,1}`,
  * Calcule `div2(x)`,
  * Puis `times2(div2(x))`.

---




