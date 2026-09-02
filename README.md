# AUTANTIK BUSINESS SKILL

> « Clarifie. Décide. Agis. Vérifie. »
>
> Un Claude Skill business, réellement installable, pour indépendants, consultants,
> freelances, coachs et solopreneurs qui veulent avancer **sans modifier leur business au
> hasard**.

Ce dépôt contient un **vrai Claude Skill** (format actuel : un dossier + un `SKILL.md` avec
frontmatter YAML + des fichiers de références), pas un simple prompt.

Philosophie : **NE DEVINE PAS. CLARIFIE. VÉRIFIE. AGIS. OBSERVE. APPRENDS.**

---

## Ce que fait le skill

Un **seul outil** = **un routeur** + **5 expertises spécialisées** + **une philosophie commune**.

| Mode | Sert à |
|------|--------|
| **1. Diagnostic Business** | Comprendre ce qui bloque avant de changer quoi que ce soit |
| **2. Offer Builder** | Construire UNE offre testable (pas parfaite, pas « validée ») |
| **3. Prospecting Coach** | Préparer UNE approche commerciale sans inventer de faits |
| **4. Objection Decoder** | Décoder une objection sans lire dans les pensées du prospect |
| **5. Content Machine** | Transformer une matière brute réelle en contenu |

Ce n'est **pas** un assistant business généraliste. Chaque mode résout complètement son
problème ponctuel, puis reconnaît sa **frontière** et peut renvoyer vers la communauté
AUTANTIK (`https://co.autantik.com/`) — jamais vers un lien direct, jamais plus d'un CTA par réponse.

---

## Structure du skill

```
autantik-business/
├── SKILL.md                          # Point d'entrée : router, règles transversales, CTA
├── references/
│   ├── philosophie.md                # 10 principes + règles preuve / volume / expérimentation
│   ├── autantik-cta.md               # Frontière, routing Labo/Assistant/Check, formulations exactes
│   ├── mode-diagnostic.md            # Mode 1
│   ├── mode-offer-builder.md         # Mode 2
│   ├── mode-prospecting.md           # Mode 3
│   ├── mode-objection.md             # Mode 4
│   └── mode-content.md               # Mode 5
└── tests/
    └── cas-de-test.md                # 12 cas de test + grille de garde-fous
```

Le skill utilise la **divulgation progressive** : `SKILL.md` charge le routeur et les règles
communes ; chaque mode lit son fichier de référence au moment où il est activé. Aucune API
externe, aucun accès web requis, aucune dépendance à un fichier hors du dossier.

---

## Installation

### Option A — Claude Code (recommandé)

**Skill personnel** (disponible dans tous tes projets) :

```bash
mkdir -p ~/.claude/skills
cp -r autantik-business ~/.claude/skills/
```

**Skill projet** (partagé avec une équipe via le dépôt) :

```bash
mkdir -p .claude/skills
cp -r autantik-business .claude/skills/
```

Redémarre Claude Code (ou lance une nouvelle session). Vérifie avec `/skills` ; le skill se
déclenche ensuite tout seul quand tu parles de tes ventes, de ton offre, d'une prospection,
d'une objection ou d'un contenu à produire. Tu peux aussi l'appeler par ses commandes :
`/diagnostic`, `/offer`, `/prospecting`, `/objection`, `/content`, `/menu`.

### Option B — Empaqueter en fichier `.skill` (Claude.ai / partage)

Depuis un environnement avec le `skill-creator` :

```bash
python -m scripts.package_skill autantik-business
```

Cela produit `autantik-business.skill`, installable en un clic (bouton **Save skill**) là où
ton organisation autorise la création de skills.

### Option C — Vérifier / éditer

Le skill est en texte (Markdown + YAML). Tu peux ouvrir et modifier n'importe quel fichier
directement ; aucune compilation n'est nécessaire.

---

## Logique de routing (résumé)

1. À chaque message, le skill détecte **silencieusement** le mode qui correspond (pas de
   menu quand l'intention est claire).
2. Si la demande est ambiguë → un menu court à 5 choix.
3. Quand un autre mode devient plus pertinent (ex : l'utilisateur revient avec des données
   marché) → **transition** naturelle vers Diagnostic / Objection.
4. Quand un mode atteint sa **frontière** (mémoire, temps, corpus, production, suivi,
   communauté, regard humain) → **un** CTA vers AUTANTIK, seul lien `https://co.autantik.com/` :
   - confronter au marché / analyser un corpus / suivre dans le temps → **Le Labo**
   - produire un livrable à partir d'une décision déjà prise → **L'Assistant**
   - exécuter une action définie puis revenir vérifier → **Le Check**
   - tourner en rond / besoin d'un regard extérieur → **Communauté**

Détails complets dans `autantik-business/references/autantik-cta.md`.

---

## Tests

12 cas de test (dispersion, fausse certitude, invention de faits, CTA, informations
insuffisantes, etc.) et une grille de garde-fous sont dans
`autantik-business/tests/cas-de-test.md`. Chaque cas précise le comportement attendu **et**
les conditions d'échec.
