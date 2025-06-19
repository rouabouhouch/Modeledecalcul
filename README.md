### 🧠 Tableau Synthèse Ultime – Machines de Turing, Classes de Langages, Problèmes, Variantes, et Clôtures

| **Catégorie**                      | **Concept**                          | **Définition / Propriété**                                             | **Exemple / Info Clé**                                        |
| ---------------------------------- | ------------------------------------ | ---------------------------------------------------------------------- | ------------------------------------------------------------- |
| 🔧 **Machines de Turing (MT)**     | Machine de Turing                    | Modèle avec bande infinie, tête lecture/écriture, règles de transition | Simule tout programme : lire/écrire/bouger/changer état       |
|                                    | Composants                           | M = (V, B, Q, q0, F, T)                                                | T(q,a) = (b, dir, q′) → écrire b, déplacer tête, changer état |
|                                    | Configuration                        | Instantané : contenu bande + position tête + état                      | (w1, q, w2)                                                   |
|                                    | Exécution                            | Passage config → config via T                                          | Si T(q,a) défini, exécution possible                          |
|                                    | MT déterministe                      | Une règle possible par (état, symbole)                                 | Un seul chemin d'exécution                                    |
|                                    | MT non déterministe                  | Plusieurs transitions possibles                                        | Exploration en arbre                                          |
| 🧪 **Langages & calculabilité**    | Langage reconnu                      | Ensemble des mots menant à un état final                               | "1010" reconnu si mène à qf                                   |
|                                    | Langage récursif (décidable)         | MT s’arrête toujours, accepte si mot ∈ L                               | Ex : vérifier parité                                          |
|                                    | Langage réc. énumérable (r.é.)       | MT s’arrête si mot ∈ L, sinon boucle ou rejette                        | Problème de l'arrêt                                           |
|                                    | Langage co-réc. énumérable (co-r.é.) | Le complément est r.é. → MT s’arrête si mot ∉ L                        | Ex : problème de vacuité                                      |
|                                    | Fonction Turing-calculable           | MT qui calcule f(x) si elle s’arrête sur x                             | f(x) = x+1                                                    |
|                                    | Thèse de Church-Turing               | Toute fonction calculable par procédure effective l’est par une MT     | MT ≡ λ-calcul ≡ fonctions récursives                          |
|                                    | MT Universelle                       | MT qui simule toute autre MT                                           | Interpréteur universel                                        |
| 💥 **Problèmes classiques**        | Problème de l’arrêt                  | Savoir si M s’arrête sur w ?                                           | Semi-décidable ✅, décidable ❌, co-semi-décidable ❌            |
|                                    | Problème de la vacuité               | Est-ce que L(M) = ∅ ?                                                  | Indécidable ❌, co-semi-décidable ✅, semi-décidable ❌          |
|                                    | Non-vacuité                          | L(M) ≠ ∅ ?                                                             | Semi-décidable ✅                                              |
|                                    | Égalité de langages r.é.             | L(M1) = L(M2) ?                                                        | Ni semi-décidable ni co-semi-décidable ❌                      |
|                                    | Égalité de fonctions Turing-calc.    | ∀x, f(x) = g(x) ?                                                      | Indécidable, même niveau                                      |
|                                    | Arrêt uniforme                       | M s’arrête sur toutes les entrées ?                                    | Non r.é., non co-r.é.                                         |
| 🧠 **Définitions logiques**        | Décidable                            | MT s’arrête toujours, accepte si et seulement si w ∈ L                 | Langage récursif                                              |
|                                    | Semi-décidable                       | MT s’arrête si w ∈ L, sinon boucle ou rejette                          | Langage récursivement énumérable                              |
|                                    | Co-semi-décidable                    | MT s’arrête si w ∉ L, sinon boucle ou rejette                          | Complément semi-décidable                                     |
|                                    | Relation fondamentale                | L décidable ⇔ L et son complément sont semi-décidables                 | Important pour preuve de décidabilité                         |
| 🔧 **Réductions**                  | Réduction pour décidabilité          | L1 ↝ L2 et L2 décidable ⇒ L1 décidable                                 | Propagation                                                   |
|                                    | Réduction pour indécidabilité        | L1 indécidable et L1 ↝ L2 ⇒ L2 indécidable                             | Propagation                                                   |
| 🧱 **Théorème de Rice**            | Propriétés non triviales             | Toute propriété non triviale sur langages r.é. est indécidable         | Ex : vacuité, égalité                                         |
| 🧩 **Classe NP**                   | NP                                   | Problèmes dont solution vérifiable en temps polynomial                 | Sudoku, SAT                                                   |
|                                    | NP-complet                           | Plus durs de NP. Résoudre un = résoudre tous                           | SAT est NP-complet                                            |
|                                    | Réduction polynomiale                | Transformer problème en un autre rapidement                            | SAT → 3SAT → Clique                                           |
|                                    | NP toujours décidable                | Tous les problèmes NP sont décidables (mais peuvent être durs)         | —                                                             |
| 🛠 **Variantes MT (équivalentes)** | Alphabet binaire uniquement          | Simulation d’une MT sur alphabet V par MT binaire                      | Codage des symboles sur k bits                                |
|                                    | Sans transition sur place            | Transition “sur place” simulée par droite puis gauche                  | États intermédiaires nécessaires                              |
|                                    | Plusieurs bandes (k)                 | Simuler k bandes sur une seule bande                                   | Encodage du contenu                                           |
|                                    | Plusieurs têtes (k)                  | MT avec k têtes simulée sur une bande unique                           | Encodage des positions                                        |
|                                    | Machines à deux piles                | MT simulée avec 2 piles (p1 inverse w1, p2 w2)                         | Déplacement = pop/push entre piles                            |
|                                    | Décidabilité arrêt 2 piles           | Même indécidabilité que MT classique                                   | Problème de l’arrêt indécidable                               |
| 📚 **Clôture des langages**        | Langages récursifs                   | Fermés sous union, intersection, complément                            | Stability des langages décidables                             |
|                                    | Langages récursivement énumérables   | Fermés sous union, intersection, mais pas complément                   | Ex : arrêt semi-décidable, mais complément non                |
|                                    | Relation clôture & décidabilité      | L et son complément semi-décidable ⇒ L est récursif                    | Important pour compréhension des classes                      |

---

### 🧠 Résumé Visuel – Inclusion des Classes

```plaintext
                   ┌─────────────────────────────┐
                   │      Langages Décidables    │  (récursifs)
                   └─────────────┬───────────────┘
                                 │
              ┌─────────────────────────────────────┐
              │ r.é. (semi-décidables)               │
              │ co-r.é. (co-semi-décidables)         │
              └─────────────────────────────────────┘
                                 │
            Problèmes non reconnaissables (ni r.é., ni co-r.é.)
```

---

