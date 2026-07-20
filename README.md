# Ma configuration Pi : context engineering pour agents de code

Ce dépôt expose la partie publique de mon `~/.pi` : une configuration orientée **maîtrise du contexte**, pas une collection de prompts pour faire du vibe coding.

L'objectif est simple : rendre les agents IA plus fiables en leur donnant un cadre de travail déterministe, versionné et auditable. Le point central est mon extension [`pi-context-tree`](https://github.com/ZEDIUM-Off/pi-context-tree), qui permet de router du contexte selon le projet, le chemin touché, l'événement agent, et la nature du travail.

## Philosophie

Je considère le coding assisté par IA comme une discipline d'ingénierie :

- le contexte doit être structuré, pas empilé dans un prompt géant ;
- les règles doivent être injectées au bon moment, pas répétées partout ;
- les agents doivent recevoir des contraintes opérationnelles, pas des intentions vagues ;
- les normes doivent être versionnées, revues et améliorées comme du code ;
- les sorties doivent rester vérifiables par lint, types, tests, review et diff.

Cette config vise les ingénieurs qui veulent piloter des agents avec précision : architecture, responsabilité, typage, boundaries, tests, refactors, gestion des changements publics, et discipline de diff.

## Ce que contient ce dépôt

- `CONTEXT.json` — configuration globale Context Tree : sources, budgets, cache, règles d'injection ;
- `norm/` — normes de code compactes, découpées par responsabilité ;
- `agent/settings.json` — préférences Pi publiques : modèle, packages, extensions ;
- `agent/extensions/` — configuration publique d'extensions ;
- `agent/skills/` — ignoré par défaut ; seuls des skills explicitement audités doivent être allowlistés.

Le cœur du système est le routage contextuel : `CONTEXT.json` déclare des sources de contexte, puis `pi-context-tree` les injecte selon les hooks appropriés (`session:start`, `agent:start`, lecture/édition de fichiers, etc.). Le dépôt public est disponible ici : [`ZEDIUM-Off/.pi`](https://github.com/ZEDIUM-Off/.pi).

## Normes injectées

Les fichiers `norm/*.md` ne sont pas de la documentation décorative. Ils sont conçus comme des contraintes courtes, impératives et actionnables pour agents. Le bundle est organisé par ordre de priorité et par responsabilité :

- `00-core.md` — densité sémantique, noms, discipline de changement ;
- `01-responsibility.md` — responsabilités, abstraction, extraction ;
- `02-contracts.md` — types, erreurs, documentation, invalid states ;
- `03-agent-behavior.md` — garde-fous agent : hypothèses, scope creep, preuves ;
- `04-agent-execution-flow.md` — boucle planifier, implémenter, vérifier, simplifier ;
- `05-patterns.md` — règles d'admission des design patterns ;
- `06-protocols.md` — refactors, API publiques, changements architecturaux ;
- `07-norm-evolution.md` — protocole de maintenance et de réorganisation des normes ;
- `08-context-injection.md` — stratégie d'injection déterministe et granularité des matches ;
- `09-agent-parallel-flow.md` — discipline de délégation et de travail en parallèle ;
- `stack-typescript.md` — règles TypeScript et JavaScript typé ;
- `stack-web.md` — règles Web, React, Vue ;
- `stack-systems.md` — règles Rust, C, C++.

L'idée n'est pas de rendre l'agent plus bavard. L'idée est de réduire l'ambiguïté : chaque règle doit prévenir un vrai mode d'échec, avoir un déclencheur identifiable, et pouvoir évoluer sans polluer les autres normes.

## Pourquoi Context Tree

Un agent efficace n'a pas besoin de tout savoir tout le temps. Il a besoin du **bon contexte au bon moment**.

`pi-context-tree` sert à transformer une configuration de contexte en contrat d'injection :

- contexte global minimal au démarrage ;
- socle agent injecté à `agent:start` pour stabiliser le comportement ;
- overlays path-aware pour les fichiers concernés ;
- overlays content-aware via `grep` quand un attribut de code le justifie ;
- règles spécialisées pour TypeScript/JavaScript, Web, systèmes, tests, API publiques et patterns ;
- budgets explicites pour éviter le bruit ;
- sources versionnées et auditables ;
- séparation entre contexte obligatoire inline et documentation optionnelle en référence.

La granularité est volontairement stricte. Une norme ne doit pas être injectée parce qu'elle existe, mais parce qu'un hook et un signal prouvent qu'elle est utile maintenant :

- `session:start` reste léger et sert surtout à exposer des références chargeables à la demande ;
- `agent:start` injecte uniquement le socle comportemental nécessaire à toute tâche agent ;
- `tool:read` sert à comprendre un fichier et à activer des doctrines liées à ses attributs réels ;
- `tool:edit` et `tool:write` servent de préflight avant mutation, quand les garde-fous doivent être présents avant le diff ;
- les `glob` ciblent une identité stable de fichier : extension, dossier, convention de test, composant, route, vue, module système ;
- les matches `grep`/regexp ciblent une preuve dans le contenu : API publique, gestion d'erreur, async, types avancés, pattern nommé, imports/exports, tests ;
- les règles larges sont démarrées tôt seulement si elles protègent la création de fichiers ou le comportement global ;
- les règles spécialisées restent derrière des matches ultra précis pour éviter d'envoyer de la doctrine TypeScript, Web, systèmes ou design patterns à un fichier qui n'en a pas besoin.

Le résultat attendu n'est pas “plus de contexte”. C'est un contexte plus explicable : pour chaque règle active, on doit pouvoir dire quel hook l'a déclenchée, quel glob ou quelle regexp l'a justifiée, et quel mode d'échec elle prévient.

C'est ma réponse au problème classique des assistants IA : trop de contexte, mauvais contexte, ou contexte non maintenu.

## Packages Pi utilisés

`agent/settings.json` référence les extensions que j'utilise dans mon workflow, notamment :

- `pi-context-tree` — routage déterministe du contexte ;
- `pi-runtime-monitor` — suivi local du PID, du CPU, de la mémoire et des sous-agents liés à la session ;
- `pi-subagents` — délégation à des sous-agents ;
- `pi-rtk-optimizer` / `pi-tool-display` — optimisation et affichage compact des sorties outils ;
- `pi-web-access` / `pi-smart-fetch` — recherche et récupération de contenu ;
- `pi-session-search` / `pi-studio` — navigation dans les sessions et environnement de travail ;
- `accordion` — gestion du contexte long par pliage et rappel ciblé ;
- `ponytail` — garde-fou contre la sur-ingénierie.

## Ce que ce dépôt n'est pas

Ce n'est pas :

- un kit de prompts magiques ;
- une config universelle à copier sans réflexion ;
- une tentative de remplacer les tests, la review ou l'architecture ;
- un setup optimisé pour générer beaucoup de code vite.

C'est une base de travail pour construire des agents plus contrôlables, plus prévisibles, et plus alignés avec des standards d'ingénierie.

## Installation sur une nouvelle machine

Si Pi n'est pas encore configuré :

```bash
git clone git@github.com:ZEDIUM-Off/.pi.git ~/.pi
```

Si `~/.pi` existe déjà :

```bash
git clone git@github.com:ZEDIUM-Off/.pi.git ~/pi-config
rsync -av ~/pi-config/ ~/.pi/
```

Ensuite, authentifier localement Pi et les providers nécessaires. Les credentials ne sont jamais synchronisés via Git.

## Sécurité

Ce dépôt est public-safe par défaut : `.gitignore` ignore tout, puis allowlist uniquement les fichiers publiables.

Ne jamais publier :

- `agent/auth.json` — OAuth/API tokens ;
- `agent/sessions/` — transcripts, prompts, chemins locaux, extraits de code privé ;
- `agent/run-history.jsonl` — historique local ;
- `agent/git/` — clones locaux ;
- `agent/bin/` — binaires téléchargés ;
- `agent/skills/` — skills privés ou liés à des outils internes, sauf allowlist explicite ;
- `pi-acp/` — mapping local de sessions ;
- caches, logs, JSONL et artefacts temporaires.

Avant un push public :

```bash
git status --short
git ls-files
gitleaks detect --redact --config .gitleaks.toml
```

Si un secret a déjà été commité, il faut le révoquer, nettoyer l'historique Git, puis seulement publier.
