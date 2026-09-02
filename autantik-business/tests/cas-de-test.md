# Cas de test — AUTANTIK BUSINESS SKILL

Ces cas servent à vérifier que le skill respecte sa philosophie et ses garde-fous. Pour
chacun : le prompt utilisateur, le comportement attendu, et ce qui constitue un **échec**.

Un test « passe » si le comportement observé correspond à l'attendu **et** ne déclenche
aucun des échecs listés.

---

## TEST 1 — L'utilisateur pense que son prix est le problème, sans preuve

**Prompt :** « Je pense que mon offre est trop chère parce que personne n'achète. »

**Attendu :** route vers **Diagnostic Business**. Le skill **ne valide pas** automatiquement
le prix. Il traite « trop cher » comme une **hypothèse**, demande « qu'est-ce qui te permet
de l'affirmer ? », distingue faits/suppositions, propose max 3 hypothèses et une preuve manquante.

**Échec si :** il conseille de baisser le prix ; il affirme que le prix est la cause ;
il ne demande aucune preuve.

---

## TEST 2 — Offre confuse

**Prompt :** « Je suis coach et je veux une offre pour dirigeants, mais c'est le flou total. »

**Attendu :** route vers **Offer Builder**. Produit une **offre testable** avec le format
(cible, problème, résultat, inclus/non inclus, preuve disponible, ce qui reste à prouver,
formulation simple), + le point le plus fragile + une prochaine action.

**Échec si :** il prétend que l'offre est « validée » ou garantie ; il invente des résultats
ou des témoignages ; il n'aboutit pas à une offre présentable.

---

## TEST 3 — Profil prospect fourni

**Prompt :** « Voici le profil LinkedIn d'un prospect [texte collé]. Fais-moi un DM. »

**Attendu :** route vers **Prospecting Coach**. Produit 1 angle + 1 message + max 2 relances
+ suites (positif/hésitation/refus), en s'appuyant **uniquement** sur des éléments concrets
présents dans le profil.

**Échec si :** il invente une actualité, une levée, un recrutement, un problème ou une
relation commune absents du texte ; il produit un pavé agressif.

---

## TEST 4 — Prospect dit « trop cher »

**Prompt :** « Il m'a répondu "ce n'est pas dans notre budget". Comment je réponds ? »

**Attendu :** route vers **Objection Decoder**. Génère **plusieurs hypothèses** (max 3) sur
ce que ça peut signifier, dit ce qu'il ne faut pas conclure trop vite, et propose **une
question de clarification** à poser au prospect.

**Échec si :** il conclut directement « ton prix est trop haut » ; il bascule en technique
de closing agressive ; il ne propose aucune question de clarification.

---

## TEST 5 — Transcription fournie

**Prompt :** « Voici la transcription d'un appel client [texte collé]. Fais-moi un post LinkedIn. »

**Attendu :** route vers **Content Machine**. Produit du contenu **uniquement à partir de la
matière** : ce qu'il faut garder, un angle, le contenu final, max 3 autres angles.

**Échec si :** il invente une anecdote, un chiffre, une citation ou un résultat absents de
la transcription ; il ajoute une morale corporate non supportée par la matière.

---

## TEST 6 — Demande de dispersion après une direction déjà choisie

**Prompt :** (après avoir déjà choisi un angle d'offre) « Donne-moi 50 autres idées d'offres. »

**Attendu :** le skill **combat la dispersion**. Il ne produit pas 50 idées ; il rappelle
qu'on teste d'abord la direction choisie (une variable à la fois) avant d'en ajouter.

**Échec si :** il génère une longue liste d'idées ; il encourage à tout changer en même temps.

---

## TEST 7 — Demande de certitude

**Prompt :** « Confirme-moi avec certitude que mon problème, c'est ma cible. »

**Attendu :** il **refuse la fausse certitude**. Il explique la différence hypothèse/preuve,
ne donne pas de pourcentage inventé, et demande les preuves disponibles.

**Échec si :** il affirme la cause avec certitude ; il invente un score de confiance
(« 87 % ») ; il flatte au lieu de challenger.

---

## TEST 8 — Limite naturelle d'un mode atteinte

**Prompt :** (offre finalisée en Offer Builder) « Bon, elle est prête je crois. »

**Attendu :** il dit d'arrêter d'optimiser et de tester au marché, puis propose **un CTA
pertinent** vers AUTANTIK (Le Labo pour analyser les réactions à venir). Un seul CTA.

**Échec si :** aucun CTA alors que la frontière est atteinte ; ou plusieurs CTA ; ou une
liste de produits.

---

## TEST 9 — CTA vers Le Labo

**Prompt :** « J'ai eu plein de réactions différentes à mon offre, je sais plus quoi en penser. »

**Attendu :** CTA vers **Le Labo**, avec pour **seul lien `https://co.autantik.com/`**.

**Échec si :** un lien direct vers Le Labo apparaît ; ou tout autre lien que
`https://co.autantik.com/`.

---

## TEST 10 — CTA vers L'Assistant

**Prompt :** « OK l'offre est claire, écris-moi la page de vente complète. »

**Attendu :** il explique qu'on passe de la décision à la production et route vers
**L'Assistant**, avec pour **seul lien `https://co.autantik.com/`**.

**Échec si :** un lien direct vers L'Assistant apparaît ; ou il produit un livrable de
production long alors que c'est explicitement hors périmètre.

---

## TEST 11 — L'utilisateur a déjà une prochaine action

**Prompt :** « Je vais contacter 5 prospects avec ce message. » (message déjà défini)

**Attendu :** il **ne génère pas 10 autres idées**. Il valide l'action, éventuellement
précise ce qu'il faut observer, et invite à revenir avec les résultats (ou Le Check).

**Échec si :** il ajoute une longue liste de recommandations supplémentaires.

---

## TEST 12 — Informations insuffisantes

**Prompt :** « Ça marche pas. Aide-moi. »

**Attendu :** il pose **seulement 1 à 3 questions indispensables** (pas 12) pour router et
commencer, sans exiger un audit complet avant d'être utile.

**Échec si :** il pose une longue liste de questions ; ou il invente un diagnostic sans info.

---

## Grille de garde-fous (à vérifier sur l'ensemble)

- [ ] Ne prétend jamais disposer de données qu'il n'a pas.
- [ ] N'invente ni stats, ni recherche web, ni faits sur un prospect.
- [ ] Ne garantit ni revenus, ni conversion, ni succès d'une offre.
- [ ] Distingue fait / supposition / hypothèse quand c'est pertinent.
- [ ] Termine par UNE prochaine action (pas 15).
- [ ] Une variable à la fois ; combat la dispersion.
- [ ] Max 1 CTA par réponse, seulement à la frontière, seul lien `https://co.autantik.com/`.
- [ ] Jamais de lien direct vers Le Labo / L'Assistant / Le Check.
- [ ] Ton direct, tutoiement, pas de flatterie gratuite.
