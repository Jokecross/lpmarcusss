# À compléter — Masterclass Black Friday 2026 (Marcuus Lawrence)

Tout se règle dans le bloc `CONFIGURATION` en bas de `index.html`, sauf mention contraire.
Pour tout retrouver : `grep -n "À COMPLÉTER\|À FOURNIR" index.html`

| Quoi | Où | État |
|---|---|---|
| ID de la VSL | `VSL.vimeo` (ou `VSL.youtube`, ou `VSL.fichier` pour un MP4) + `VSL.format` (`'16 / 9'` ou `'9 / 16'`) | à venir |
| Base des leads | `SUPABASE_URL` + `SUPABASE_ANON_KEY` (clé anon, jamais service_role) | CRM différé : rien n'est envoyé tant que c'est vide |
| Client « Marcuus Lawrence » / offre « Masterclass Black Friday 2026 » | n'existe pas dans le schéma des templates (un projet Supabase par client) | à décider avec le CRM |
| Colonnes de suivi | `COLONNES_SUIVI = true` une fois les colonnes `ref`, `utm_*` créées | sinon `ref` → `source`, UTM → `page_url` |
| Pixel Meta | `PIXELS.meta` (PageView + Lead à l'envoi) | à fournir |
| Pixel TikTok | `PIXELS.tiktok` (page + SubmitForm à l'envoi) | à fournir |
| E-mail de contact | `CONTACT_EMAIL` | à fournir (la page KOS affiche contact@marcuus-lawrence.com) |
| CGU, Politique de confidentialité, CGV | `LIENS.cgu`, `LIENS.confidentialite`, `LIENS.cgv` | à fournir (le lien de la case de consentement suit `LIENS.confidentialite`) |
| Photos de Marcuus | `img/marcuus-2017-2026.webp` + `img/avatar-marcuus-v2.webp` (signature du mot de Marcuus : sa photo de profil du 29/10, recadrée sans « 1ER NOV ») | **provisoire** : découpée dans une capture d'écran de sa page ; remplacer par les originaux (même cadrage, fond #FAEFE9) |
| Image de partage | `og:image` dans `<head>` | mettre l'adresse absolue quand le domaine est connu |
| Indexation Google | `<meta name="robots" content="noindex">` + en-tête `X-Robots-Tag` dans `vercel.json` | noindex par défaut, à confirmer |

## Études de cas et captures (28/10)

- **5 études de cas vidéo** (Nicolas, Fousseny, Antoine, Malory, Yass & Marine) : vidéos de `Etude de cas élèves /`
  recompressées dans `videos/`, miniatures dans `img/etude-*.webp`. Textes résumés depuis les fiches envoyées par Martin.
- **7 captures Shopify** de `Résultats élèves Screen/` → `img/resultat-01…07.webp`, recadrées sur les chiffres ;
  nom de boutique flouté sur la n° 2 (« Eluva ») et sur la miniature de Yass & Marine (« Viatalia »).
  ⚠️ La vidéo de Yass & Marine montre le nom de leur boutique en clair (enregistrement d'écran) : non retouchée.
- ⚠️ **Conflit avec les règles du brief** (« jamais de montant de gain, ni 1 000 € par jour ») : ces sections affichent
  des chiffres d'affaires par jour. Garde-fous en place : « de CA », mention « accompagnement de Marcuus, pas la
  masterclass seule », « pas des bénéfices, pas représentatifs, aucune garantie ». **À valider avec l'équipe de Marcuus.**
- Les médias bruts restent hors git (`.gitignore`).

## Textes à valider

- **Section 03** (« Marcuus te montre ») : commentaire `<!-- Contenu à valider avec l'équipe de Marcuus -->` dans le code.
- **Mots en corail** : le gras du brief a été perdu au copier-coller, les mots mis en corail sont un choix
  (hero : « Black Friday 2026 », « moins que le prix d'un McDo » ; C : « 27 novembre » ; etc.).
- **Titres ajoutés** (aucun dans le brief) : « Ce que tu reçois », « Comment ça se passe », « Tes questions »,
  « Enchanté, moi c'est Marcuus Lawrence ».
- **Orthographe du nom** : « Marcuus » partout depuis le brief du 29/10.

## DA

Relevée sur les captures de la page KOS (la page n'est pas accessible directement : go.marcuus-lawrence.com
redirige vers un autre tunnel). Les valeurs sont dans `:root`. Police des titres : Lora 700 resserrée, la plus
proche de la serif de Marcuus parmi les Google Fonts ; à remplacer si son équipe donne le nom exact.
