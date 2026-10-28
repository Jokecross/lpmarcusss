# Page de vente — Masterclass Black Friday 2026 (Marcus Lawrence)

Page secondaire de Marcus Lawrence : une masterclass tournée pour le Black Friday 2026,
extension de KOS 2.0. Un seul objectif : le formulaire. Un setter rappelle le lead dans
les 10 minutes.

Fichier HTML unique (CSS et JS dans la page, sans build), sur la mécanique de la page
Mexed (`~/Page de vente Mexed`, non modifiée) : formulaire, indicatifs + E.164, anti-spam,
suivi des sources, envoi dans la table `leads` de Supabase.

```
index.html        la page
img/              photo de Marcus (provisoire), captures de résultats, miniatures, image de partage
videos/           études de cas recompressées (H.264, démarrage rapide)
favicon.svg
vercel.json       URLs propres, liens courts /nom, noindex
A-COMPLETER.md    tout ce qui attend un contenu réel
```

## En local

```
python3 -m http.server 8090
```

puis http://localhost:8090. Les liens courts `/nom` ne marchent qu'une fois sur Vercel
(utiliser `?ref=nom` en local).

## Comment circule un lead

```
Bouton « JE VEUX MON ACCÈS »  →  modale du formulaire (la page ne défile pas)
        │  POST /rest/v1/leads avec la clé anon
        ▼
Table public.leads (schéma du CRM Mexed)  →  setters
        │
        └──►  dans la modale, le formulaire laisse la place à « C'est envoyé ! »
              + Lead (Meta) / SubmitForm (TikTok) si les pixels sont renseignés
```

- Téléphone au format E.164, +33 par défaut.
- **Suivi** : `?ref=lea` (ou `?src=lea`, ou `/lea`) et les UTM sont retenus 30 jours
  dans le navigateur et remplis dans des champs cachés. Sans colonnes dédiées
  (`COLONNES_SUIVI = false`), `ref` part dans `source` et les UTM dans `page_url`.
- **Anti-spam** : champ leurre `company` ; rempli, la page simule un succès sans rien envoyer.

## Preuves

- **Études de cas** : carrousel de 5 vidéos verticales (glisser sur mobile, flèches sur ordinateur).
  Seule la miniature est chargée ; la vidéo part au clic, une seule joue à la fois.
- **Captures** : mosaïque (2 colonnes sur mobile, 3 au-delà), agrandissement au clic.
- Les médias bruts (`Résultats élèves Screen/`, `Etude de cas élèves /`) restent hors git.

## Charte (relevée sur la page KOS 2.0)

| Rôle | Valeur |
|---|---|
| Fond | blanc, sections pêche `#FAEFE9` en fondu |
| Titres | Lora 700, noir, lettres resserrées ; mots clés corail `#E86C46` |
| Texte | Roboto, `#2F2F2F` ; listes des cartes `#4A3F3B` |
| Bouton | dégradé `#1EC01E` → `#0E9C0E`, capitales blanches, chevron, ombre verte |
| Cartes | blanc, rayon 24 px, bordure `#EDEDED` ; positive : bordure `#F5BCAC` + voile pêche |
| Icônes | croix sur rond `#EDEDED`, coche sur rond `#D7F4E5` (grande : `#4CD08A`) |
| Pied de page | `#191919`, texte blanc |

Le haut de page est un titre texte « MASTERCLASS BLACK FRIDAY 2026 » construit comme le
logo de Marcus (trait, petit mot, gros mot, pastille corail), sans le logo KOS.

Mobile d'abord (testé à 375 px) ; à partir de 760 px les cartes passent en colonnes,
et au-delà de 1000 px la barre CTA fixe disparaît. Sur mobile, la barre apparaît après le
hero et se cache sur le dernier appel et le pied de page. `…/#formulaire` ouvre la modale à l'arrivée.
