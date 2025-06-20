### Expressions du λ-calcul pur (syntaxique) :

Une **expression λ** $E$ est définie inductivement par :

1. **Variable** :

   $$
   x \quad \text{où } x \in \text{ensemble des variables}
   $$

2. **Abstraction** :

   $$
   \lambda x . E
   $$

   (fonction anonyme qui prend un argument $x$ et retourne l’expression $E$)

3. **Application** :

   $$
   (E_1 \; E_2)
   $$

   (application de la fonction $E_1$ à l’argument $E_2$)

---

### Résumé simple

* **Variables** : symboles $x, y, z, \ldots$
* **Fonctions** : $\lambda x . E$
* **Appels** : $(E_1 E_2)$

---

### Exemple d’expressions

* $x$ (variable)
* $\lambda x . x$ (identité)
* $\lambda x . \lambda y . x$ (fonction constante)
* $(\lambda x . x) y$ (application)
* $(\lambda x . (x x)) (\lambda x . (x x))$ (auto-application)

---

### Important :

* Pas de types (c’est du **λ-calcul pur**, sans typage)
* Pas d’autres opérateurs ou constantes (tout est construit à partir de ces règles)
* Parenthèses servent à clarifier l’ordre, mais souvent on omet les parenthèses internes selon la convention.

---

Si tu veux, je peux t’expliquer aussi comment ça se réduit ou comment on manipule ces expressions.
