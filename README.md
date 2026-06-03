# AD-Compagnon

> « **Ce que votre Active Directory ne vous a jamais dit.** »

**AD-Compagnon** est un magazine technique francophone, mensuel, entièrement consacré à la sécurité d'Active Directory. Chaque numéro part d'une **idée reçue** du quotidien des administrateurs — un raisonnement rassurant mais faux — et la démonte de bout en bout, jusqu'à montrer comment refermer la porte.

Le magazine est rédigé par **Yeni DOUKAKAS** et s'adresse aux ingénieurs IT francophones qui veulent comprendre leur annuaire en profondeur, sans jargon inutile et sans approximations.

---

## La ligne éditoriale

- **Partir d'une idée reçue, pas d'une TTP.** Le point d'entrée est toujours une phrase qu'on entend en réunion : un raisonnement plausible, partagé, et faux. Cette manière de poser le problème distingue AD-Compagnon des dépêches de menaces et des manuels d'attaque classiques.
- **Profondeur technique, sans condescendance.** Les protocoles, les attributs, les outils réels (BloodHound, Rubeus, Certipy, impacket, mimikatz...) sont présentés en pleine clarté, avec les lignes de commande exactes. Le but est de former des praticiens lucides — défenseurs comme attaquants — pas de raconter des histoires.
- **Toujours un arc complet.** Toute attaque exposée est suivie, dans le même numéro, de sa détection et de sa remédiation. Pas d'exception. Le magazine ne livre jamais une demi-fiche.
- **Ton pédagogue, chaleureux, parfois drôle.** Jamais condescendant, jamais arrogant. Chaque numéro est conçu pour qu'un expert chevronné y trouve un « je ne savais pas ça » — et ait envie de le tester immédiatement.
- **Domaines fictifs uniquement.** Toutes les captures, commandes et schémas utilisent le domaine maison `adcompagnon.lab` (NetBIOS `ADCOMPAGNON`). Aucun nom d'infrastructure réelle n'apparaît, sous aucun prétexte.

---

## Public visé

| Cible | Ce qu'AD-Compagnon lui apporte |
|---|---|
| **Administrateurs systèmes, ingénieurs IT** *(cible première)* | Une lecture rigoureuse du fonctionnement réel de l'annuaire, et les bons gestes pour le durcir. |
| **Pentesters, red teamers, analystes forensic** | Des chaînes d'attaque exposées avec leurs outils et leurs traces, pour des opérations lucides. |
| **Analystes SOC** | Les bons Event IDs, les requêtes de chasse, et les signatures à inscrire dans la supervision. |
| **Décideurs IT et RSSI** | Une rubrique dédiée par numéro, qui formule la bonne question à poser à l'équipe. |

---

## Structure d'une fiche

Chaque numéro est un PDF A4 de **6 pages**, organisé en trois niveaux balisés :

- **Niveau 1 — Le déclic.** L'idée reçue, l'analogie du quotidien, l'impact métier. Tout le jargon est expliqué. Conçu pour être compris par un lecteur non spécialiste.
- **Niveau 2 — Le mécanisme.** Le fonctionnement réel du protocole, de l'attribut, ou du flux d'authentification concerné. Schémas vectoriels à l'appui.
- **Niveau 3 — La salle des machines.** Trois gestes, toujours dans le même ordre :
  - ① **Vérifier** — la commande de diagnostic, à exécuter chez soi.
  - ② **Comprendre l'attaque** — la chaîne déroulée, du repérage à la chute.
  - ③ **Corriger et détecter** — les gestes de remédiation, et les événements à surveiller.

Sept rubriques récurrentes ponctuent la collection : *L'idée reçue*, *Sous l'écorce*, *La commande du jour*, *Vu sur le terrain*, *Le coin du décideur*, *L'énigme du Compagnon*, *Le glossaire*. Une énigme cross-référence parfois un numéro antérieur — la collection se répond d'un mois sur l'autre, ce qui récompense la lecture en série.

---

## Les numéros parus

### N°01 — Tout le monde peut fabriquer un ordinateur
**Axe A · Les comptes et les groupes** · Mai 2026

> « Seuls les administrateurs peuvent ajouter une machine au domaine. »

Démontage de l'attribut `ms-DS-MachineAccountQuota`, ce réglage hérité de l'an 2000 qui autorise par défaut tout utilisateur authentifié à créer jusqu'à dix comptes ordinateurs — sans privilège, sans validation, sans alerte. De la délégation Kerberos basée sur les ressources (RBCD) à l'usurpation **noPac** (CVE-2021-42278/42287), comment un détail oublié devient une amorce d'attaque — et comment refermer la porte en deux gestes, sans budget.

📄 [`AD-Compagnon_N01_quota-machines.pdf`](./pdf/AD-Compagnon_N01_quota-machines.pdf) · 🎴 [Carrousel LinkedIn](./pdf/AD-Compagnon_N01_carrousel-linkedin.pdf)

---

### N°02 — Le serveur le plus anodin de votre parc
**Axe B · Kerberos** · Juin 2026

> « Ce serveur n'héberge pas de données sensibles — il n'est pas critique. »

La criticité d'un serveur ne tient pas à ce qu'il stocke, mais à ce qu'il laisse passer. La **délégation Kerberos non contrainte** — un réglage parfaitement légitime d'origine — accumule en mémoire le TGT de chaque compte qui se connecte, contrôleurs de domaine compris. Du repérage BloodHound à la coercition d'un DC, jusqu'au DCSync, ce numéro montre comment un simple compte de serveur applicatif devient un Tier 0 silencieux — et comment l'éradiquer.

📄 [`AD-Compagnon_N02_delegation-kerberos.pdf`](./pdf/AD-Compagnon_N02_delegation-kerberos.pdf) · 🎴 [Carrousel LinkedIn](./pdf/AD-Compagnon_N02_carrousel-linkedin.pdf)

---

### N°03 — Le trousseau de clés que personne n'a inventorié
**Axe C · Les permissions de l'annuaire** · Juillet 2026

> « Mes groupes d'administration sont verrouillés — seuls les admins peuvent y toucher. »

Qui peut modifier un objet d'Active Directory ne dépend pas du groupe auquel on appartient, mais d'une **liste de contrôle d'accès** gravée sur l'objet lui-même. Le numéro fondateur sur les ACL et les ACE : `GenericAll`, `WriteDACL`, `WriteOwner`, le mécanisme `AdminSDHolder`, et l'idée que tout compte peut, par une ACE mal placée, *devenir* administrateur sans jamais y avoir été ajouté. L'énigme du numéro — l'héritage des permissions — sert de pivot à plusieurs numéros suivants.

📄 [`AD-Compagnon_N03_permissions-acl.pdf`](./pdf/AD-Compagnon_N03_permissions-acl.pdf) · 🎴 [Carrousel LinkedIn](./pdf/AD-Compagnon_N03_carrousel-linkedin.pdf)

---

### N°04 — L'autorité qui signe des badges à votre place
**Axe D · Les services de certificats AD CS** · Août 2026

> « Notre PKI, c'est pour le HTTPS et le Wi-Fi — un sujet réseau, pas un sujet sécurité. »

Un certificat délivré par AD CS n'est pas qu'un cadenas pour le navigateur : c'est une **pièce d'identité** que le domaine accepte pour authentifier un compte, via PKINIT. Le numéro décortique la faille **ESC1** — les quatre conditions qui transforment un modèle de certificat en faille d'élévation directe — et son cousin **ESC8**, qui ignore complètement les modèles en relayant l'authentification vers l'interface web d'inscription. L'extension SID (KB5014754) est présentée comme garde-fou.

📄 [`AD-Compagnon_N04_adcs-certificats.pdf`](./pdf/AD-Compagnon_N04_adcs-certificats.pdf) · 🎴 [Carrousel LinkedIn](./pdf/AD-Compagnon_N04_carrousel-linkedin.pdf)

---

### N°05 — Le mot de passe qui ne change jamais
**Axe E · Les comptes de service** · Septembre 2026

> « Le mot de passe de ce compte de service est long et compliqué — il est inattaquable. »

La complexité ne protège pas un compte porteur d'un **SPN** : avec Kerberos, quiconque réclame un ticket pour ce compte peut l'emporter chez soi et le casser **hors ligne**, sans verrouillage, sans alerte. Le **Kerberoasting** est décortiqué étape par étape — récolte avec Rubeus ou impacket, cassage hashcat — et la vraie parade, les **gMSA** (comptes de service gérés au mot de passe de 240 octets, renouvelé par AD), est posée comme cible à atteindre. L'énigme — le Kerberoasting *ciblé* via greffe d'un SPN — renvoie explicitement au N°03.

📄 [`AD-Compagnon_N05_kerberoasting.pdf`](./pdf/AD-Compagnon_N05_kerberoasting.pdf) · 🎴 [Carrousel LinkedIn](./pdf/AD-Compagnon_N05_carrousel-linkedin.pdf)

---

### N°06 — La porte entre deux domaines, restée ouverte
**Axe F · Les relations d'approbation** · Octobre 2026

> « Cette vieille approbation avec l'autre domaine ? Un détail historique, ça ne nous concerne plus. »

Une relation d'approbation n'est pas une poignée de main : c'est un **pont d'authentification permanent**, qui transporte la liste des SID — et le SID History. Compromettre le domaine d'en face — souvent plus petit, plus ancien, moins surveillé — suffit à forger un ticket inter-royaume et à devenir administrateur du vôtre. Le numéro présente le rôle du **filtrage de SID** (et son absence par défaut entre domaines d'une même forêt), avec une attention particulière à l'erreur de lecture la plus fréquente : confondre le sens d'une approbation et le sens de l'accès.

📄 [`AD-Compagnon_N06_approbations.pdf`](./pdf/AD-Compagnon_N06_approbations.pdf) · 🎴 [Carrousel LinkedIn](./pdf/AD-Compagnon_N06_carrousel-linkedin.pdf)

---

### N°07 — Le coffre-fort qui se copie à distance
**Axe G · La réplication d'annuaire** · Novembre 2026

> « Pour voler les mots de passe du domaine, il faut accéder physiquement à un contrôleur de domaine. »

La réplication est une fonction d'administration **à distance**. Deux droits étendus précis (`Get-Changes` et `Get-Changes-All`) suffisent à demander à un contrôleur de domaine de répliquer tous ses secrets, en se faisant passer pour un pair. C'est **DCSync**. La cible privilégiée — le compte `krbtgt` — ouvre la voie au **Golden Ticket**, ce TGT forgé valable des années. Le numéro insiste sur la double réinitialisation de krbtgt comme seul moyen d'invalider la compromission. L'énigme — qui possède *réellement* le droit de réplication — renvoie au N°03.

📄 [`AD-Compagnon_N07_replication-dcsync.pdf`](./pdf/AD-Compagnon_N07_replication-dcsync.pdf) · 🎴 [Carrousel LinkedIn](./pdf/AD-Compagnon_N07_carrousel-linkedin.pdf)

---

### N°08 — L'outil qui configure tout — et exécute tout
**Axe H · Les stratégies de groupe** · Décembre 2026

> « Modifier une stratégie de groupe, c'est réservé aux administrateurs — c'est verrouillé. »

Une **GPO** vit en deux endroits : un objet `GPC` dans l'annuaire, et un dossier `GPT` sur le partage `SYSVOL`. Un droit d'écriture sur l'un ou l'autre — souvent une délégation oubliée — suffit à pousser une tâche planifiée immédiate sur toutes les machines liées. Le numéro présente la chaîne d'abus avec **SharpGPOAbuse** et `pyGPOAbuse`, et révèle la « troisième porte » : un droit d'écriture sur l'attribut `gPLink` d'une OU, qui permet de *lier* à cette OU une GPO malveillante qu'on contrôle ailleurs — sans modifier aucune GPO existante. Verrouiller l'écriture des GPO ne suffit pas : il faut aussi verrouiller le droit de lier.

📄 [`AD-Compagnon_N08_strategies-groupe.pdf`](./pdf/AD-Compagnon_N08_strategies-groupe.pdf) · 🎴 *Carrousel LinkedIn — à venir*

---

## Déclinaison LinkedIn

Chaque numéro est accompagné, en parallèle de la fiche PDF, d'un **carrousel LinkedIn** et de son **texte de post**.

- **Format technique.** Carrousel carré 1080×1080 px, 9 slides, exporté en PDF (format accepté par LinkedIn comme document).
- **Trame fixe.** (1) Couverture avec l'idée reçue ; (2) la révélation « En réalité… » ; (3) l'analogie du quotidien ; (4-5) le mécanisme réel ; (6) la chaîne d'attaque résumée ; (7) la correction en trois gestes ; (8) le coin du décideur ; (9) appel à lire la fiche complète.
- **Principe de lisibilité.** Peu de texte par slide, hiérarchie visuelle nette, lecture au pouce sur mobile. Le carrousel donne envie de lire la fiche ; il ne la remplace pas.
- **Texte d'accompagnement.** Une accroche qui interpelle, trois à quatre lignes qui plantent l'enjeu, un appel à l'action vers la fiche, quelques hashtags ciblés.

Les sept premiers carrousels (N°01 à N°07) sont disponibles dans la collection ; les textes de post sont rassemblés dans [`AD-Compagnon_posts-linkedin.md`](./AD-Compagnon_posts-linkedin.md).

---

## La charte graphique

La collection s'appuie sur une charte graphique unifiée — palette teal et ambre, polices Baloo 2 / Nunito / Cascadia Code, mascotte « le pic éclaireur ». Toute évolution se fait dans une feuille de style partagée (`adcompagnon.css` pour les fiches, `carrousel.css` pour les carrousels), garantissant la cohérence visuelle de l'ensemble.

📄 [`AD-Compagnon_Charte-graphique_v1.pdf`](./pdf/AD-Compagnon_Charte-graphique_v1.pdf)

---

## À propos

**AD-Compagnon** est un projet éditorial indépendant. Le magazine est rédigé par **Yeni DOUKAKAS**, sans rattachement institutionnel ni publicitaire. Sa raison d'être : combler le vide d'une littérature francophone trop superficielle sur la sécurité d'Active Directory, en livrant des contenus à la fois rigoureux et lisibles.

Le magazine paraît mensuellement, sous forme de PDF téléchargeable. Les numéros sont libres de lecture et de partage à des fins de formation et de sensibilisation.

---

## Comment lire

Les fiches sont en PDF A4 portrait, conçues pour l'écran comme pour l'impression. Les commandes PowerShell qu'elles contiennent sont conçues pour être copiées et exécutées depuis un poste d'administration disposant du module **RSAT**. Toutes les illustrations utilisent exclusivement le domaine fictif `adcompagnon.lab` — aucun copier-coller ne révélera une infrastructure réelle.

---

## Prochain numéro

**N°09 — LAPS et les mots de passe locaux : le trousseau d'administrateur que tout le monde partageait.** Comment un même mot de passe d'administrateur local sur tout le parc transforme un poste compromis en passe universel — et pourquoi LAPS n'est pas qu'une bonne pratique parmi d'autres.

---

<sub>« Ce que votre Active Directory ne vous a jamais dit. » — Yeni DOUKAKAS, AD-Compagnon.</sub>
