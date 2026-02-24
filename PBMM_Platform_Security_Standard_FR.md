# PROTÉGÉ B / INTÉGRITÉ MOYENNE / DISPONIBILITÉ MOYENNE
# NORME DE SÉCURITÉ OPÉRATIONNELLE
## Plateforme de zone d'atterrissage Azure

**Classification :** PROTÉGÉ B  
**Version du document :** 1.0  
**Date d'entrée en vigueur :** [DATE]  
**Date de révision :** [DATE + 1 AN]  
**Propriétaire du document :** [NOM DE L'ORGANISATION]  
**Autorité de sécurité :** [NOM/TITRE]

---

# CONTRÔLE DU DOCUMENT

| Version | Date | Auteur | Description |
|---------|------|--------|-------------|
| 1.0 | [DATE] | [AUTEUR] | Version initiale |

**Liste de distribution :**
- Autorité de sécurité de la plateforme
- Opérations de la plateforme infonuagique
- Centre des opérations de sécurité
- Administrateurs des locataires clients
- Comité consultatif des changements
- Audit interne

---

# TABLE DES MATIÈRES

1. Introduction
2. Objet et portée
3. Profil de sécurité infonuagique
4. Cadre de gouvernance
5. Modèle de responsabilité partagée
6. Cadre de gestion des risques
7. Gestion des identités et des accès
8. Sécurité du réseau
9. Protection des systèmes et des communications
10. Gestion de la configuration
11. Gestion des changements
12. Audit et responsabilisation
13. Intervention en cas d'incident
14. Planification de la continuité
15. Gestion des vulnérabilités
16. Protection des données
17. Surveillance continue
18. Exploitation de la plateforme
19. Sécurité de l'intégration des clients
20. Rôles et responsabilités
21. Gestion des exceptions
22. Vérification de la conformité
23. Maintenance du document
Annexe A : Correspondance des contrôles ITSG-33
Annexe B : Exigences en matière de preuves
Annexe C : Modèle d'héritage des contrôles
Annexe D : Glossaire

---

# 1. INTRODUCTION

## 1.1 Contexte

Le gouvernement du Canada a établi des exigences de sécurité pour les systèmes d'information infonuagiques par l'intermédiaire du cadre de sécurité infonuagique du Centre canadien pour la cybersécurité (CCCS) et du catalogue de contrôles de sécurité ITSG-33. Les organisations exploitant des systèmes d'information qui traitent, stockent ou transmettent des renseignements Protégé B DOIVENT mettre en œuvre des contrôles de sécurité proportionnels à la sensibilité des renseignements et aux exigences opérationnelles du système.

La présente norme de sécurité opérationnelle établit les politiques de sécurité, les procédures et les contrôles techniques pour la plateforme de zone d'atterrissage Azure exploitée par [NOM DE L'ORGANISATION]. La plateforme fournit des services d'infrastructure infonuagique fondamentaux prenant en charge plusieurs charges de travail clients selon un modèle d'architecture en étoile (hub-and-spoke).

## 1.2 Structure du document

Ce document est organisé selon les sections suivantes :

- **Sections 1 à 3** établissent le contexte, la portée et le profil de sécurité du document
- **Sections 4 à 6** définissent les cadres de gouvernance, de responsabilité partagée et de gestion des risques
- **Sections 7 à 17** précisent les exigences de mise en œuvre des contrôles de sécurité
- **Sections 18 à 19** définissent les procédures opérationnelles et l'intégration des clients
- **Sections 20 à 23** établissent les rôles, les exceptions, la conformité et la maintenance
- **Annexes** fournissent les correspondances de contrôles, les exigences en matière de preuves et les documents d'appui

## 1.3 Cadre de conformité

La présente norme s'aligne sur les cadres et exigences suivants :

- **ITSG-33 :** Gestion des risques liés à la sécurité des TI : Une approche axée sur le cycle de vie
- **Profil infonuagique PBMM du CCCS :** Protégé B / Intégrité moyenne / Disponibilité moyenne
- **Politique sur la sécurité du gouvernement du Conseil du Trésor**
- **Directive sur la gestion de la sécurité**
- **Norme sur la catégorisation de sécurité du Conseil du Trésor**
- **Documentation de conformité de Microsoft Azure pour le gouvernement du Canada**

## 1.4 Terminologie

Dans l'ensemble du présent document, la terminologie suivante DOIT être interprétée comme défini :

- **DOIT / OBLIGATOIRE :** Indique une exigence obligatoire
- **DEVRAIT :** Indique une pratique recommandée pouvant faire l'objet d'une dérogation avec justification documentée
- **PEUT :** Indique une pratique facultative
- **Plateforme :** L'infrastructure de zone d'atterrissage Azure et les services partagés
- **Client :** Un locataire ou propriétaire de charge de travail utilisant les services de la plateforme
- **Spoke :** Un abonnement client connecté au hub de la plateforme

---

# 2. OBJET ET PORTÉE

## 2.1 Objet

L'objet de la présente norme de sécurité opérationnelle est de :

a) Définir le cadre de gouvernance de la sécurité pour la plateforme de zone d'atterrissage Azure;

b) Établir les exigences de contrôle de sécurité alignées sur l'ITSG-33 et le profil infonuagique PBMM du CCCS;

c) Documenter les procédures de sécurité opérationnelle pour la gestion de la plateforme;

d) Définir le modèle de responsabilité partagée entre l'équipe de la plateforme, les clients et Microsoft Azure;

e) Fournir une base pour les activités d'évaluation et d'autorisation de sécurité (EAS);

f) Permettre une posture de sécurité cohérente pour toutes les charges de travail hébergées sur la plateforme.

## 2.2 Portée

### 2.2.1 Dans la portée

La présente norme s'applique à :

a) **Infrastructure de la plateforme :**
   - Hiérarchie des groupes de gestion et structure des abonnements
   - Réseau virtuel hub et services de connectivité
   - Pare-feu Azure et contrôles de sécurité réseau
   - Infrastructure centralisée de journalisation et de surveillance
   - Services de gestion des identités et des accès
   - Outils de sécurité (Microsoft Defender pour le cloud, Microsoft Sentinel)
   - Abonnements de gestion de la plateforme
   - Infrastructure de gestion des clés

b) **Exploitation de la plateforme :**
   - Déploiement et configuration de la plateforme
   - Gestion des changements pour les composants de la plateforme
   - Surveillance de la sécurité et intervention en cas d'incident
   - Intégration et retrait des clients
   - Maintenance et correction de la plateforme

c) **Personnel de la plateforme :**
   - Administrateurs de la plateforme
   - Personnel des opérations de sécurité
   - Personnel des opérations réseau
   - Personnel du bureau de service ayant accès à la plateforme

### 2.2.2 Hors de la portée

La présente norme ne couvre pas :

a) Les contrôles de sécurité des charges de travail clients (définis dans la documentation de sécurité propre aux charges de travail)
b) Les exigences de sécurité au niveau des applications
c) La classification et le traitement des données clients (responsabilité du client)
d) La sécurité des appareils des utilisateurs finaux
e) La sécurité physique des centres de données Microsoft (responsabilité de Microsoft)

### 2.2.3 Périmètre du système

Le périmètre d'autorisation de cette plateforme comprend :

- Locataire Azure : [ID DU LOCATAIRE]
- Groupes de gestion : Plateforme, Zones d'atterrissage, Bac à sable, Mis hors service
- Abonnements de la plateforme : Identité, Connectivité, Gestion, Sécurité
- Abonnements spoke : [CONVENTION DE NOMMAGE DES CLIENTS]
- Régions Azure : Canada Centre (principal), Canada Est (secondaire)

## 2.3 Public cible

Ce document est destiné aux :

- Autorité de sécurité de la plateforme et évaluateurs de sécurité
- Équipes d'ingénierie et d'exploitation de la plateforme infonuagique
- Personnel du Centre des opérations de sécurité
- Représentants de la sécurité des clients
- Auditeurs internes et externes
- Membres du Comité consultatif des changements

---

# 3. PROFIL DE SÉCURITÉ INFONUAGIQUE

## 3.1 Catégorisation de sécurité

La plateforme de zone d'atterrissage Azure a été catégorisée conformément à la Norme sur la catégorisation de sécurité du Conseil du Trésor :

| Objectif de sécurité | Catégorie | Justification |
|---------------------|-----------|---------------|
| Confidentialité | Protégé B | La plateforme héberge des systèmes clients traitant des renseignements Protégé B |
| Intégrité | Moyenne | La compromission de l'intégrité de la plateforme pourrait affecter plusieurs charges de travail clients |
| Disponibilité | Moyenne | La plateforme soutient les opérations commerciales avec des exigences de reprise définies |

**Profil global :** Protégé B / Intégrité moyenne / Disponibilité moyenne (PBMM)

## 3.2 Alignement sur le profil infonuagique du CCCS

Cette plateforme fonctionne selon le profil infonuagique PBMM du CCCS, qui exige :

a) La mise en œuvre des contrôles de sécurité ITSG-33 au niveau de référence PBMM;
b) L'utilisation d'un service infonuagique évalué par le CCCS (Microsoft Azure Canada);
c) La résidence des données sur le territoire canadien;
d) Le chiffrement des données au repos et en transit;
e) La surveillance et la journalisation centralisées de la sécurité;
f) Une gouvernance formelle de la sécurité et une gestion des risques.

## 3.3 Modèle de service infonuagique

La plateforme utilise des composants d'infrastructure en tant que service (IaaS) et de plateforme en tant que service (PaaS) de Microsoft Azure. Le modèle de responsabilité partagée (section 5) définit les responsabilités en matière de sécurité entre le fournisseur infonuagique, l'équipe de la plateforme et les clients.

## 3.4 Résidence des données

Toutes les données de la plateforme DOIVENT résider dans les régions Azure canadiennes :

- **Région principale :** Canada Centre (Toronto)
- **Région secondaire :** Canada Est (Québec)

Les données NE DOIVENT PAS être répliquées vers, traitées dans ou accessibles depuis des régions situées hors du Canada, sauf autorisation explicite obtenue par le processus d'exception défini à la section 21.

## 3.5 Mesures de protection infonuagiques

La plateforme met en œuvre les mesures de protection infonuagiques du gouvernement du Canada :

| Mesure de protection | Mise en œuvre |
|---------------------|---------------|
| MP-1 : Protéger les comptes et identités des utilisateurs | Entra ID avec AMF, PIM, accès conditionnel |
| MP-2 : Gérer les accès | RBAC, principe du moindre privilège, accès JAT |
| MP-3 : Sécuriser les points de terminaison | Intégration de Defender pour point de terminaison |
| MP-4 : Comptes de surveillance d'entreprise | Comptes d'urgence avec surveillance |
| MP-5 : Emplacement des données | Configuration des régions canadiennes uniquement |
| MP-6 : Protection des données au repos | Chiffrement géré par la plateforme |
| MP-7 : Protection des données en transit | Application de TLS 1.2+ |
| MP-8 : Segmenter et séparer | Architecture réseau en étoile |
| MP-9 : Services de sécurité réseau | Pare-feu Azure, NSG, points de terminaison privés |
| MP-10 : Services de cyberdéfense | Defender pour le cloud, Sentinel |
| MP-11 : Journalisation et surveillance | Log Analytics central, Sentinel |
| MP-12 : Configuration des places de marché infonuagiques | Accès restreint à la place de marché |

---

# 4. CADRE DE GOUVERNANCE

## 4.1 Structure de gouvernance de la sécurité

### 4.1.1 Autorité organisationnelle

L'autorité de sécurité de [NOM DE L'ORGANISATION] est responsable de la posture de sécurité globale de la plateforme de zone d'atterrissage Azure. L'autorité de sécurité DOIT :

a) Approuver la présente norme de sécurité opérationnelle et les révisions subséquentes;
b) Accepter le risque résiduel associé à l'exploitation de la plateforme;
c) Autoriser l'intégration des clients à la plateforme;
d) Examiner et approuver les exceptions de sécurité;
e) Commander des évaluations de sécurité périodiques.

### 4.1.2 Autorité de sécurité de la plateforme

L'autorité de sécurité de la plateforme a la responsabilité déléguée de :

a) La gouvernance quotidienne de la sécurité de la plateforme;
b) La mise en œuvre et la surveillance des contrôles de sécurité;
c) La gestion et l'intervention en cas d'incident de sécurité;
d) La surveillance continue de la conformité;
e) La coordination de la sécurité avec les clients.

### 4.1.3 Organes de gouvernance

Les organes de gouvernance suivants soutiennent la sécurité de la plateforme :

**Comité consultatif des changements (CCC)**
- Examine et approuve les changements à la plateforme
- Évalue l'impact sur la sécurité des changements proposés
- Se réunit hebdomadairement ou au besoin pour les changements d'urgence

**Groupe de travail sur la sécurité**
- Examine la posture de sécurité et les indicateurs
- Traite les constatations de sécurité et les vulnérabilités
- Se réunit toutes les deux semaines

**Revue des opérations de la plateforme**
- Examine les indicateurs opérationnels et les incidents
- Traite les problèmes de capacité et de performance
- Se réunit hebdomadairement

## 4.2 Cadre stratégique

### 4.2.1 Hiérarchie des politiques

La présente norme s'inscrit dans la hiérarchie des politiques suivante :

1. Politiques et directives du Conseil du Trésor
2. Politique de sécurité ministérielle
3. La présente norme de sécurité opérationnelle
4. Procédures opérationnelles de la plateforme
5. Exigences de sécurité des clients

En cas de conflit, les politiques de niveau supérieur DOIVENT prévaloir.

### 4.2.2 Documentation connexe

La présente norme est soutenue par :

- Document d'architecture de la plateforme
- Rapport d'évaluation de la sécurité
- Registre des risques
- Plan d'intervention en cas d'incident
- Plan de continuité des activités
- Guide d'intégration des clients

## 4.3 Exigences de conformité

### 4.3.1 Conformité réglementaire

La plateforme DOIT maintenir la conformité avec :

- Loi sur la protection des renseignements personnels (Canada)
- Loi sur l'accès à l'information
- Loi sur la preuve au Canada
- Législation provinciale sur la protection de la vie privée, le cas échéant

### 4.3.2 Conformité contractuelle

La plateforme DOIT maintenir la conformité avec :

- Conditions de l'entente d'entreprise Microsoft
- Ententes de service avec les clients
- Ententes avec les fournisseurs tiers

### 4.3.3 Surveillance de la conformité

La conformité DOIT être surveillée par :

a) Conformité automatisée aux politiques à l'aide d'Azure Policy;
b) Tableau de bord de conformité réglementaire de Microsoft Defender pour le cloud;
c) Examens de conformité trimestriels;
d) Évaluations de sécurité annuelles.

---

# 5. MODÈLE DE RESPONSABILITÉ PARTAGÉE

## 5.1 Aperçu

La sécurité infonuagique fonctionne selon un modèle de responsabilité partagée où les obligations de sécurité sont réparties entre Microsoft Azure (fournisseur infonuagique), l'équipe de la plateforme et les locataires clients. Une délimitation claire des responsabilités est essentielle au maintien de la posture de sécurité et à l'évitement des lacunes dans la mise en œuvre des contrôles.

## 5.2 Responsabilités de Microsoft Azure

Microsoft Azure est responsable de la sécurité DU nuage :

### 5.2.1 Sécurité physique
- Contrôles d'accès physique aux centres de données
- Contrôles environnementaux (alimentation, refroidissement, extinction des incendies)
- Destruction des supports physiques
- Surveillance de la sécurité des installations

### 5.2.2 Sécurité de l'infrastructure
- Sécurité et isolation de l'hyperviseur
- Sécurité de l'infrastructure réseau
- Sécurité et maintenance du matériel
- Sécurité du micrologiciel et du BIOS

### 5.2.3 Sécurité de la plateforme
- Mises à jour de sécurité des services Azure
- Disponibilité de la plateforme Azure
- Sécurité du réseau dorsal mondial
- Protection DDoS à la périphérie du réseau

### 5.2.4 Conformité
- Attestation SOC 2 Type II
- Certification ISO 27001
- Évaluation de sécurité infonuagique du CCCS
- Autorisation FedRAMP (référence)

## 5.3 Responsabilités de l'équipe de la plateforme

L'équipe de la plateforme est responsable de la sécurité DANS le nuage au niveau de la plateforme :

### 5.3.1 Identité et accès
- Configuration et sécurité du locataire
- Gestion des identités privilégiées
- Politiques d'accès conditionnel
- Exigences d'authentification
- Gestion des principaux de service
- Gestion des comptes d'urgence

### 5.3.2 Sécurité du réseau
- Architecture du réseau virtuel hub
- Configuration et règles du pare-feu Azure
- Configuration DNS
- Infrastructure des points de terminaison privés
- Segmentation du réseau entre les clients
- Connectivité VPN/ExpressRoute

### 5.3.3 Outils de sécurité
- Configuration de Microsoft Defender pour le cloud
- Déploiement et règles de Microsoft Sentinel
- Alertes de sécurité et intervention
- Gestion des vulnérabilités pour les composants de la plateforme
- Application des références de sécurité

### 5.3.4 Journalisation et surveillance
- Espace de travail Log Analytics central
- Paramètres de diagnostic pour les ressources de la plateforme
- Rétention et archivage des journaux
- Surveillance de la performance de la plateforme
- Surveillance des événements de sécurité

### 5.3.5 Gouvernance
- Structure des groupes de gestion
- Définitions et affectations d'Azure Policy
- Rôles RBAC de la plateforme
- Approvisionnement des abonnements
- Normes de nommage et d'étiquetage des ressources
- Gestion des coûts au niveau de la plateforme

### 5.3.6 Opérations
- Gestion des changements de la plateforme
- Intervention en cas d'incident de la plateforme
- Sauvegarde et reprise de la plateforme
- Gestion de Key Vault pour les secrets de la plateforme
- Gestion des certificats

## 5.4 Responsabilités des locataires clients

Les locataires clients sont responsables de la sécurité DANS le nuage au niveau de la charge de travail :

### 5.4.1 Sécurité des applications
- Sécurité du code d'application
- Authentification et autorisation des applications
- Chiffrement au niveau des applications
- Gestion des vulnérabilités des applications
- Journalisation des applications

### 5.4.2 Sécurité des données
- Classification des données
- Décisions de chiffrement des données au-delà des valeurs par défaut de la plateforme
- Contrôles d'accès aux données
- Rétention et élimination des données
- Sauvegarde des données (au-delà de la référence de la plateforme)

### 5.4.3 Sécurité des charges de travail
- Sécurité et correction des machines virtuelles
- Sécurité des conteneurs
- Configuration de la sécurité des bases de données
- Contrôles d'accès au stockage
- Groupes de sécurité réseau propres aux charges de travail

### 5.4.4 Identité
- Principaux de service d'application
- Utilisation d'identités gérées
- RBAC propre aux charges de travail
- Gestion des accès des utilisateurs d'applications

### 5.4.5 Conformité
- Exigences de conformité propres aux charges de travail
- Évaluations de sécurité des applications
- Exigences d'audit propres aux clients
- Procédures de traitement des données

## 5.5 Matrice des responsabilités

| Domaine de contrôle | Microsoft | Plateforme | Client |
|---------------------|-----------|------------|--------|
| Sécurité physique du centre de données | ● | ○ | ○ |
| Hyperviseur et matériel | ● | ○ | ○ |
| Infrastructure réseau | ● | ◐ | ○ |
| Configuration de l'identité du locataire | ○ | ● | ○ |
| Gestion des accès privilégiés | ○ | ● | ◐ |
| Sécurité du réseau hub | ○ | ● | ○ |
| Sécurité du réseau spoke | ○ | ◐ | ● |
| Outils de sécurité de la plateforme | ○ | ● | ○ |
| Outils de sécurité des charges de travail | ○ | ◐ | ● |
| Infrastructure de journalisation centrale | ○ | ● | ○ |
| Journalisation des charges de travail | ○ | ○ | ● |
| Gestion des changements de la plateforme | ○ | ● | ○ |
| Gestion des changements des charges de travail | ○ | ○ | ● |
| Sécurité des applications | ○ | ○ | ● |
| Classification des données | ○ | ○ | ● |

**Légende :** ● Principal | ◐ Partagé | ○ Non responsable

## 5.6 Héritage des contrôles

Les charges de travail clients héritent de certains contrôles de sécurité de la plateforme :

### 5.6.1 Contrôles hérités (complets)
Contrôles entièrement hérités par les charges de travail clients :
- Sécurité physique
- Configuration de la sécurité du locataire
- Sécurité du périmètre réseau
- Infrastructure de journalisation centrale
- Infrastructure de surveillance de la sécurité
- Gestion des correctifs de la plateforme

### 5.6.2 Contrôles hérités (partiels)
Contrôles partiellement hérités, nécessitant une mise en œuvre par le client :
- Sécurité réseau (NSG au niveau spoke requis)
- Gestion des accès (RBAC de charge de travail requis)
- Gestion des vulnérabilités (correction des charges de travail requise)
- Sauvegarde (sauvegarde propre aux charges de travail requise)

### 5.6.3 Contrôles mis en œuvre par le client
Contrôles nécessitant une mise en œuvre complète par le client :
- Sécurité des applications
- Chiffrement des données au-delà des valeurs par défaut
- Journalisation propre aux charges de travail
- Contrôles d'accès aux applications

---

# 6. CADRE DE GESTION DES RISQUES

## 6.1 Approche de gestion des risques

La plateforme emploie une approche de gestion des risques continue alignée sur la méthodologie du cycle de vie de l'ITSG-33 :

1. **Identifier :** Identifier les menaces, les vulnérabilités et les exigences de sécurité
2. **Évaluer :** Évaluer la probabilité et l'impact des risques
3. **Atténuer :** Mettre en œuvre des contrôles pour réduire les risques à des niveaux acceptables
4. **Surveiller :** Surveiller en continu le risque résiduel et l'efficacité des contrôles
5. **Rapporter :** Rapporter l'état des risques aux organes de gouvernance

## 6.2 Évaluation des risques

### 6.2.1 Évaluation des menaces

L'évaluation des menaces de la plateforme considère :

a) **Menaces externes :**
   - Acteurs étatiques ciblant les systèmes gouvernementaux
   - Organisations criminelles cybernétiques
   - Hacktivistes
   - Attaquants opportunistes

b) **Menaces internes :**
   - Initiés malveillants
   - Utilisateurs négligents
   - Identifiants compromis

c) **Menaces environnementales :**
   - Interruptions de service infonuagique
   - Pannes régionales
   - Compromission de la chaîne d'approvisionnement

### 6.2.2 Évaluation des vulnérabilités

L'évaluation des vulnérabilités est effectuée par :

a) Analyse automatisée des vulnérabilités (Microsoft Defender)
b) Analyse de conformité de la configuration (Azure Policy)
c) Tests d'intrusion (annuels)
d) Examens de l'architecture de sécurité

### 6.2.3 Calcul du risque

Le risque est calculé selon la formule :

**Risque = Probabilité × Impact**

| Probabilité | Description |
|-------------|-------------|
| 5 - Presque certain | Devrait se produire dans la plupart des circonstances |
| 4 - Probable | Se produira probablement dans la plupart des circonstances |
| 3 - Possible | Pourrait se produire à un moment donné |
| 2 - Peu probable | Pourrait se produire à un moment donné |
| 1 - Rare | Ne peut se produire que dans des circonstances exceptionnelles |

| Impact | Description |
|--------|-------------|
| 5 - Grave | Dommages critiques aux opérations, violation importante des données |
| 4 - Majeur | Impact opérationnel majeur, incident de sécurité important |
| 3 - Modéré | Impact opérationnel modéré, incident de sécurité contenu |
| 2 - Mineur | Impact opérationnel mineur, incident de sécurité limité |
| 1 - Négligeable | Impact négligeable |

## 6.3 Traitement des risques

### 6.3.1 Options de traitement

Les risques identifiés DOIVENT être traités selon une ou plusieurs des options suivantes :

a) **Atténuer :** Mettre en œuvre des contrôles pour réduire la probabilité ou l'impact du risque
b) **Transférer :** Transférer le risque par l'assurance ou des arrangements contractuels
c) **Accepter :** Accepter le risque résiduel avec approbation documentée
d) **Éviter :** Éliminer la source du risque

### 6.3.2 Acceptation du risque

L'acceptation du risque exige :

a) Documentation dans le registre des risques
b) Identification du propriétaire du risque
c) Approbation au niveau d'autorité approprié :
   - Risque faible : Autorité de sécurité de la plateforme
   - Risque moyen : Autorité de sécurité
   - Risque élevé/critique : Autorité exécutive

### 6.3.3 Surveillance des risques

Le risque résiduel DOIT être surveillé par :

a) Examens trimestriels du registre des risques
b) Indicateurs et KPI de sécurité
c) Analyse des tendances des incidents
d) Analyse des tendances des vulnérabilités
e) État de conformité

## 6.4 Registre des risques

La plateforme maintient un registre des risques documentant :

- Identifiant du risque
- Description du risque
- Source de la menace
- Vulnérabilité
- Contrôles existants
- Cotes de probabilité et d'impact
- Score de risque
- Décision de traitement
- Plan de traitement
- Propriétaire du risque
- Date de révision

Le registre des risques DOIT être révisé trimestriellement et mis à jour à la suite de changements importants ou d'incidents.

---

# 7. GESTION DES IDENTITÉS ET DES ACCÈS

## 7.1 Aperçu

La gestion des identités et des accès (GIA) est fondamentale pour la sécurité de la plateforme. La plateforme met en œuvre un cadre GIA complet utilisant Microsoft Entra ID (anciennement Azure Active Directory) avec des contrôles de défense en profondeur.

**Familles de contrôles ITSG-33 :** AC (Contrôle d'accès), IA (Identification et authentification)

## 7.2 Gestion des identités

### 7.2.1 Fournisseur d'identité

Microsoft Entra ID DOIT être le fournisseur d'identité faisant autorité pour tous les accès à la plateforme. Toutes les identités accédant aux ressources de la plateforme DOIVENT être :

a) Provisionnées par des processus de cycle de vie des identités approuvés;
b) Affectées à des groupes appropriés en fonction des exigences du rôle;
c) Soumises à des examens d'accès réguliers;
d) Désactivées ou supprimées lors d'un changement de rôle ou d'une cessation d'emploi.

### 7.2.2 Types d'identités

La plateforme prend en charge les types d'identités suivants :

**Identités utilisateur**
- Administrateurs de la plateforme
- Personnel des opérations de sécurité
- Administrateurs des locataires clients
- Comptes d'urgence

**Identités de service**
- Identités gérées (privilégiées)
- Principaux de service (lorsque l'identité gérée n'est pas disponible)
- Inscriptions d'applications

### 7.2.3 Cycle de vie des identités

**Provisionnement**
Le provisionnement des utilisateurs DOIT suivre le principe du moindre privilège :
a) Demandes d'accès soumises par un processus approuvé
b) Approbation du gestionnaire requise
c) Examen de sécurité pour les accès privilégiés
d) Provisionnement juste-à-temps lorsque possible

**Maintenance**
a) Examens d'accès trimestriels pour tous les comptes privilégiés
b) Examens d'accès annuels pour les comptes standards
c) Les changements de rôle déclenchent un examen d'accès
d) Les comptes inactifs sont désactivés après 90 jours

**Déprovisionnement**
a) Révocation immédiate lors de la cessation d'emploi
b) Suppression de l'accès dans les 24 heures suivant un changement de rôle
c) La mise hors service des comptes de service suit le processus de changement

### 7.2.4 Comptes d'urgence

Des comptes d'accès d'urgence DOIVENT être maintenus pour les scénarios où l'authentification normale n'est pas disponible :

a) Minimum de deux comptes d'urgence
b) Comptes infonuagiques uniquement (non fédérés)
c) Exclus des politiques d'accès conditionnel
d) Identifiants stockés dans un coffre-fort physique sécurisé
e) L'utilisation déclenche une alerte immédiate
f) L'utilisation est journalisée et examinée
g) Les identifiants sont renouvelés après chaque utilisation
h) Vérification trimestrielle de la fonctionnalité du compte

## 7.3 Authentification

### 7.3.1 Authentification multifacteur

L'authentification multifacteur (AMF) DOIT être appliquée pour toute authentification interactive :

a) Tous les comptes utilisateur nécessitent l'AMF sans exception
b) Les méthodes résistantes à l'hameçonnage sont privilégiées (FIDO2, Windows Hello)
c) L'application Microsoft Authenticator comme second facteur standard
d) Les SMS et appels vocaux sont interdits pour les comptes privilégiés
e) Les paramètres AMF par utilisateur NE DOIVENT PAS être utilisés (accès conditionnel appliqué)

### 7.3.2 Accès conditionnel

Les politiques d'accès conditionnel DOIVENT appliquer les exigences d'authentification en fonction du contexte :

**Politiques de base (tous les utilisateurs)**
- Exiger l'AMF pour toutes les applications infonuagiques
- Bloquer les protocoles d'authentification hérités
- Exiger un appareil conforme ou joint à Hybrid Azure AD pour l'accès au portail
- Bloquer l'accès depuis des emplacements non autorisés

**Politiques d'accès privilégié**
- Exiger l'AMF résistante à l'hameçonnage pour les portails administratifs
- Exiger un appareil conforme
- Bloquer l'accès depuis l'extérieur du Canada
- Durée de session maximale de 4 heures
- Exiger une réauthentification pour les actions sensibles

**Politiques basées sur le risque**
- Exiger l'AMF pour un risque de connexion moyen
- Bloquer un risque de connexion élevé (exiger la réinitialisation du mot de passe)
- Bloquer un risque utilisateur élevé (exiger une réinitialisation sécurisée du mot de passe)

### 7.3.3 Politique de mot de passe

Pour les comptes utilisant l'authentification par mot de passe :

a) Minimum de 14 caractères
b) Exigences de complexité activées
c) Expiration du mot de passe désactivée (selon les directives du NIST) avec détection des violations
d) Liste de mots de passe interdits activée
e) Réinitialisation du mot de passe en libre-service activée avec vérification renforcée

### 7.3.4 Authentification des services

Les principaux de service et les identités gérées DOIVENT :

a) Utiliser l'authentification par certificat ou l'identité gérée lorsque possible
b) Renouveler les secrets tous les 90 jours maximum si basés sur des secrets
c) Utiliser des identifiants fédérés lorsque pris en charge
d) Ne pas utiliser de secrets de longue durée lorsque des alternatives existent

## 7.4 Autorisation

### 7.4.1 Contrôle d'accès basé sur les rôles

Le contrôle d'accès basé sur les rôles (RBAC) Azure DOIT être utilisé pour toutes les autorisations :

a) Pas d'affectations directes aux utilisateurs (groupes uniquement)
b) Principe du moindre privilège appliqué
c) Rôles personnalisés minimisés (privilégier les rôles intégrés)
d) Affectations de rôles documentées et justifiées

### 7.4.2 Gestion des identités privilégiées

Azure AD Privileged Identity Management (PIM) DOIT être utilisé pour tous les rôles privilégiés :

**Affectations éligibles**
- Rôles privilégiés affectés comme « éligibles » et non « actifs »
- L'activation nécessite une justification
- L'activation nécessite l'AMF
- Durée d'activation limitée (maximum 8 heures)

**Flux d'approbation**
- L'administrateur général nécessite une approbation
- L'administrateur de la sécurité nécessite une approbation
- Les autres rôles privilégiés nécessitent une justification

**Examens d'accès**
- Examens d'accès mensuels pour l'administrateur général
- Examens d'accès trimestriels pour les autres rôles privilégiés
- Les examinateurs sont indépendants des titulaires de rôles

### 7.4.3 Rôles privilégiés

Les rôles suivants sont classés comme privilégiés et nécessitent PIM :

**Niveau 0 (privilège le plus élevé)**
- Administrateur général
- Administrateur de rôles privilégiés
- Administrateur de la sécurité
- Administrateur Exchange (le cas échéant)
- Administrateur SharePoint (le cas échéant)

**Niveau 1 (privilège élevé)**
- Administrateur d'utilisateurs
- Administrateur d'applications
- Administrateur d'applications infonuagiques
- Administrateur d'authentification
- Administrateur de groupes
- Administrateur Intune (le cas échéant)

**Niveau 2 (privilège de plateforme)**
- Propriétaire d'abonnement
- Contributeur d'abonnement (abonnements de plateforme)
- Administrateur Key Vault
- Contributeur réseau (abonnement hub)

### 7.4.4 Accès aux abonnements

L'accès aux abonnements DOIT suivre ces principes :

a) Affectations au niveau du groupe de gestion pour un accès étendu
b) Affectations au niveau de l'abonnement pour un accès spécifique
c) Les affectations au niveau du groupe de ressources sont évitées sauf pour l'accès délégué aux clients
d) Les affectations directes aux ressources sont interdites

## 7.5 Procédures de contrôle d'accès

### 7.5.1 Processus de demande d'accès

1. Le demandeur soumet une demande d'accès avec justification commerciale
2. Le gestionnaire approuve le besoin commercial
3. Le propriétaire des données/ressources approuve la portée de l'accès
4. La sécurité examine les demandes d'accès privilégié
5. L'accès est provisionné via l'appartenance au groupe
6. Le demandeur reconnaît sa responsabilité d'accès

### 7.5.2 Processus d'examen d'accès

1. L'examinateur reçoit une notification d'examen d'accès
2. L'examinateur valide le besoin commercial continu
3. L'examinateur approuve ou refuse l'accès
4. L'accès refusé est supprimé automatiquement
5. L'absence de réponse entraîne la suppression de l'accès
6. L'achèvement est rapporté à la gouvernance

### 7.5.3 Processus d'accès d'urgence

1. L'urgence est déclarée par le personnel autorisé
2. Les identifiants d'urgence sont récupérés du stockage sécurisé
3. L'utilisation du compte d'urgence est journalisée avec justification
4. Le travail d'urgence est effectué
5. La session est terminée
6. Un rapport d'incident est déposé
7. Les identifiants sont renouvelés
8. L'utilisation est examinée par l'autorité de sécurité

---

# 8. SÉCURITÉ DU RÉSEAU

## 8.1 Aperçu

La sécurité du réseau met en œuvre les principes de défense en profondeur par la segmentation, la connectivité contrôlée et l'inspection du trafic. La plateforme emploie une architecture en étoile avec des services de sécurité centralisés.

**Familles de contrôles ITSG-33 :** SC (Protection des systèmes et des communications)

## 8.2 Architecture réseau

### 8.2.1 Modèle en étoile (Hub-and-Spoke)

La plateforme met en œuvre une topologie réseau en étoile :

**Réseau virtuel hub**
- Services de connectivité et de sécurité centralisés
- Pare-feu Azure pour l'inspection du trafic
- Passerelle VPN/ExpressRoute pour la connectivité hybride
- Azure Bastion pour l'accès administratif sécurisé
- Infrastructure DNS
- Sous-réseau des services partagés

**Réseaux virtuels spoke**
- Hébergement des charges de travail clients
- Appairés au hub pour la connectivité
- Isolés des autres spokes
- Soumis aux politiques du pare-feu hub

### 8.2.2 Segmentation du réseau

La segmentation du réseau DOIT être mise en œuvre par :

a) Réseaux virtuels distincts par client (isolation des spokes)
b) Sous-réseaux au sein des spokes pour les niveaux de charge de travail
c) Groupes de sécurité réseau (NSG) sur tous les sous-réseaux
d) Pare-feu Azure pour le trafic inter-spoke et sortant
e) Points de terminaison privés pour les services PaaS

### 8.2.3 Gestion des adresses IP

L'adressage IP DOIT être géré centralement :

a) Plan d'adressage IP documenté
b) Espaces d'adressage non chevauchants
c) Plages réservées pour la croissance future
d) L'équipe de la plateforme contrôle toutes les affectations d'adresses

## 8.3 Contrôle du flux de trafic

### 8.3.1 Trafic entrant

Le trafic entrant depuis Internet DOIT :

a) Passer par le pare-feu Azure ou un WAF approuvé
b) Être limité aux flux explicitement approuvés
c) Être journalisé et surveillé
d) Utiliser TLS 1.2 ou supérieur pour les services chiffrés

### 8.3.2 Trafic sortant

Le trafic sortant vers Internet DOIT :

a) Être acheminé via le pare-feu Azure
b) Être filtré par des règles d'application
c) Utiliser des listes d'autorisation basées sur les FQDN (pas de destinations génériques)
d) Être journalisé pour l'analyse de sécurité
e) Bloquer les destinations malveillantes connues (renseignements sur les menaces)

### 8.3.3 Trafic est-ouest

Le trafic entre les spokes DOIT :

a) Être acheminé via le pare-feu Azure
b) Être explicitement autorisé par les règles du pare-feu
c) Être refusé par défaut entre les spokes clients
d) Être journalisé pour l'analyse de sécurité

### 8.3.4 Trafic de gestion

Le trafic administratif DOIT :

a) Utiliser Azure Bastion pour l'accès aux VM (pas d'IP publiques sur les VM)
b) Utiliser des points de terminaison privés pour la gestion PaaS
c) Utiliser un sous-réseau de gestion dédié lorsque requis
d) Être journalisé et surveillé

## 8.4 Pare-feu Azure

### 8.4.1 Configuration du pare-feu

Le pare-feu Azure DOIT être déployé avec :

a) SKU Premium pour l'inspection TLS et l'IDPS
b) Politique de pare-feu pour la gestion centralisée des règles
c) Renseignements sur les menaces activés en mode Alerte et Refus
d) IDPS en mode Alerte et Refus
e) Proxy DNS activé

### 8.4.2 Hiérarchie des règles

Les règles du pare-feu DOIVENT être organisées :

1. **Règles de plateforme :** Exigences d'infrastructure
2. **Règles de sécurité :** Blocage des menaces, listes de refus
3. **Règles clients :** Règles d'application propres aux clients
4. **Refus par défaut :** Refus implicite pour le trafic non correspondant

### 8.4.3 Gestion des règles

Les modifications aux règles du pare-feu DOIVENT :

a) Suivre le processus de gestion des changements
b) Inclure un examen de sécurité pour les nouvelles règles d'autorisation
c) Documenter la justification commerciale
d) Utiliser une portée de moindre privilège
e) Inclure une expiration pour les règles temporaires

## 8.5 Groupes de sécurité réseau

### 8.5.1 Exigences NSG

Les groupes de sécurité réseau DOIVENT être appliqués à tous les sous-réseaux :

a) Refus par défaut du trafic entrant depuis Internet
b) Règles d'autorisation explicites pour le trafic requis
c) Journaux de flux NSG activés
d) Règles documentées et justifiées

### 8.5.2 Meilleures pratiques NSG

a) Utiliser des balises de service au lieu d'adresses IP lorsque possible
b) Utiliser des groupes de sécurité d'application pour le regroupement des charges de travail
c) Éviter les règles trop permissives (pas de sources 0.0.0.0/0)
d) Examen régulier des règles NSG

## 8.6 Connectivité privée

### 8.6.1 Points de terminaison privés

Les points de terminaison privés DOIVENT être utilisés pour les services PaaS :

a) Comptes de stockage
b) Key Vault
c) Azure SQL Database
d) Azure Container Registry
e) Autres services PaaS pris en charge

L'accès public DOIT être désactivé lorsque des points de terminaison privés sont mis en œuvre.

### 8.6.2 Connectivité hybride

La connectivité aux réseaux sur site DOIT :

a) Utiliser ExpressRoute (privilégié) ou une passerelle VPN
b) Chiffrer le trafic en transit
c) Être documentée dans l'architecture réseau
d) Suivre les principes de connectivité de moindre privilège

### 8.6.3 Configuration DNS

Le DNS DOIT être configuré pour prendre en charge les points de terminaison privés :

a) Zones DNS privées pour les services Azure
b) Transfert DNS vers les sites sur place lorsque requis
c) Proxy DNS du pare-feu Azure pour la résolution DNS des spokes
d) Infrastructure DNS gérée centralement

## 8.7 Surveillance du réseau

### 8.7.1 Journalisation des flux

Les journaux de flux réseau DOIVENT être collectés :

a) Journaux de flux NSG activés sur tous les NSG
b) Journaux de flux envoyés à Log Analytics
c) Traffic Analytics activé
d) Rétention minimale de 90 jours

### 8.7.2 Journalisation du pare-feu

Les journaux du pare-feu Azure DOIVENT inclure :

a) Journaux des règles d'application
b) Journaux des règles réseau
c) Journaux des renseignements sur les menaces
d) Journaux IDPS
e) Journaux du proxy DNS

### 8.7.3 Surveillance du réseau

La surveillance du réseau DOIT inclure :

a) Connection Monitor pour les tests de connectivité
b) Network Performance Monitor le cas échéant
c) Alertes sur les refus du pare-feu et les détections de menaces
d) Analyse régulière des modèles de trafic

---

# 9. PROTECTION DES SYSTÈMES ET DES COMMUNICATIONS

## 9.1 Aperçu

La protection des systèmes et des communications assure la confidentialité et l'intégrité des informations en transit et au repos par le chiffrement et la configuration sécurisée.

**Familles de contrôles ITSG-33 :** SC (Protection des systèmes et des communications)

## 9.2 Chiffrement au repos

### 9.2.1 Chiffrement du stockage

Toutes les données au repos DOIVENT être chiffrées :

a) Chiffrement du service de stockage Azure (SSE) activé
b) Disques gérés chiffrés par défaut
c) Chiffrement transparent des données (TDE) SQL Database activé
d) Données de sauvegarde chiffrées

### 9.2.2 Gestion des clés

Les clés de chiffrement DOIVENT être gérées selon la sensibilité des données :

**Clés gérées par la plateforme (par défaut)**
- Microsoft gère les clés de chiffrement
- Acceptable pour la plupart des charges de travail
- Pas de surcharge de gestion des clés pour le client

**Clés gérées par le client (lorsque requis)**
- Le client contrôle les clés dans Azure Key Vault
- Requis pour des exigences de conformité spécifiques
- Politiques de rotation des clés appliquées

### 9.2.3 Key Vault

Azure Key Vault DOIT être utilisé pour la gestion des secrets :

a) Key Vault dédié par périmètre de sécurité
b) Politiques d'accès ou RBAC pour l'autorisation
c) Suppression réversible et protection contre le vidage activées
d) Point de terminaison privé pour l'accès réseau
e) Journalisation des diagnostics activée

## 9.3 Chiffrement en transit

### 9.3.1 Sécurité de la couche de transport

TLS DOIT être appliqué pour toutes les données en transit :

a) Version TLS minimale 1.2
b) TLS 1.0 et 1.1 désactivés
c) Suites de chiffrement fortes uniquement
d) Validation des certificats appliquée

### 9.3.2 Trafic interne

Le trafic au sein de la plateforme DOIT :

a) Utiliser TLS pour la communication service à service
b) Utiliser TLS pour les connexions aux bases de données
c) Utiliser TLS pour l'accès au stockage
d) Utiliser IPsec pour les tunnels VPN

### 9.3.3 Trafic externe

Le trafic vers/depuis des parties externes DOIT :

a) Utiliser TLS 1.2 ou supérieur
b) Utiliser des certificats d'AC de confiance
c) Mettre en œuvre la surveillance des certificats pour l'expiration

## 9.4 Configuration sécurisée

### 9.4.1 Références de sécurité

Les ressources de la plateforme DOIVENT respecter les références de sécurité :

a) Microsoft Cloud Security Benchmark comme référence
b) Recommandations du CIS Azure Foundations Benchmark
c) Azure Policy pour l'application de la conformité
d) Évaluation régulière de la conformité aux références

### 9.4.2 Configuration des ressources

La configuration sécurisée par défaut DOIT inclure :

**Machines virtuelles**
- Disques chiffrés
- Pas d'adresses IP publiques
- NSG sur le sous-réseau
- Defender pour serveurs activé
- Mises à jour automatiques activées

**Comptes de stockage**
- HTTPS uniquement
- TLS minimum 1.2
- Point de terminaison privé
- Suppression réversible activée
- Versionnage des blobs activé

**Azure SQL**
- TDE activé
- TLS minimum 1.2
- Point de terminaison privé
- Audit activé
- Defender pour SQL activé

**Key Vault**
- Suppression réversible activée
- Protection contre le vidage activée
- Point de terminaison privé
- Journalisation des diagnostics activée

---

# 10. GESTION DE LA CONFIGURATION

## 10.1 Aperçu

La gestion de la configuration assure une configuration cohérente, sécurisée et documentée de la plateforme par l'infrastructure en tant que code et la conformité automatisée.

**Familles de contrôles ITSG-33 :** CM (Gestion de la configuration)

## 10.2 Configuration de référence

### 10.2.1 Normes de configuration

Les normes de configuration de la plateforme DOIVENT être documentées pour :

a) Structure des groupes de gestion
b) Configuration des abonnements
c) Architecture réseau
d) Configuration des outils de sécurité
e) Configuration de la journalisation
f) Configuration de l'identité

### 10.2.2 Référence de configuration

La référence de configuration DOIT :

a) Être versionnée dans un dépôt Git
b) Représenter l'état sécurisé approuvé
c) Être la source de vérité pour les déploiements
d) Inclure toute la configuration de l'infrastructure

## 10.3 Infrastructure en tant que code

### 10.3.1 Exigences IaC

Toute l'infrastructure de la plateforme DOIT être déployée à l'aide de l'infrastructure en tant que code :

a) Terraform ou Bicep comme outils IaC approuvés
b) Pas de déploiements manuels via le portail pour les ressources de la plateforme
c) Tous les changements de configuration via le code
d) Révision du code requise avant la fusion

### 10.3.2 Dépôt de code

Le code IaC DOIT être géré dans des dépôts approuvés :

a) Dépôt Azure DevOps ou GitHub
b) Protection des branches activée
c) Demande de tirage requise pour les changements
d) Révision et approbation requises
e) Intégration CI/CD pour le déploiement

### 10.3.3 Normes des modules

Les modules IaC DOIVENT suivre les normes :

a) Entrées et sorties documentées
b) Valeurs par défaut de sécurité configurées
c) Exigences d'étiquetage appliquées
d) Conventions de nommage appliquées
e) Versionnés

## 10.4 Azure Policy

### 10.4.1 Cadre de politiques

Azure Policy DOIT appliquer la conformité de la configuration :

a) Politiques affectées au niveau du groupe de gestion
b) Héritées par les abonnements et les ressources
c) Effets Audit et Refus utilisés de manière appropriée
d) Exemptions documentées et limitées dans le temps

### 10.4.2 Catégories de politiques

Les politiques DOIVENT couvrir :

**Politiques de sécurité**
- Exigences de chiffrement
- Exigences de sécurité réseau
- Exigences d'identité
- Exigences de journalisation

**Politiques de gouvernance**
- Régions autorisées (Canada uniquement)
- Types de ressources autorisés
- Conventions de nommage
- Exigences d'étiquetage

**Politiques de coûts**
- Restrictions de SKU
- Application des instances réservées
- Alertes de budget

### 10.4.3 Conformité aux politiques

La conformité aux politiques DOIT être surveillée :

a) Tableau de bord de conformité de Defender pour le cloud
b) Rapports de conformité réguliers
c) Processus de remédiation de la non-conformité
d) Processus d'examen des exemptions

## 10.5 Contrôle des changements

### 10.5.1 Processus de changement de configuration

Les changements de configuration DOIVENT suivre le processus de gestion des changements (section 11) :

a) Demande de changement soumise
b) Évaluation d'impact effectuée
c) Examen de sécurité pour les changements liés à la sécurité
d) Approbation obtenue
e) Changement mis en œuvre via IaC
f) Vérification effectuée
g) Changement documenté

### 10.5.2 Détection de la dérive

La dérive de configuration DOIT être détectée et corrigée :

a) Surveillance de l'état Terraform
b) Surveillance de la conformité Azure Policy
c) Audits de configuration réguliers
d) Alertes de dérive automatisées
e) Procédures de remédiation de la dérive

---

# 11. GESTION DES CHANGEMENTS

## 11.1 Aperçu

La gestion des changements assure des changements contrôlés, documentés et réversibles à la plateforme tout en maintenant la sécurité et la disponibilité.

**Familles de contrôles ITSG-33 :** CM (Gestion de la configuration)

## 11.2 Catégories de changements

### 11.2.1 Changements standards

Changements pré-approuvés, à faible risque et de routine :
- Provisionnement de spoke client (utilisant le modèle approuvé)
- Ajouts de règles de pare-feu (dans la portée approuvée)
- Provisionnement d'accès utilisateur
- Activités de maintenance de routine

Les changements standards nécessitent une procédure documentée mais pas d'approbation du CCC.

### 11.2.2 Changements normaux

Changements nécessitant une évaluation et une approbation :
- Déploiement de nouvelles capacités de plateforme
- Changements à l'architecture réseau
- Changements à la configuration de sécurité
- Déploiements de nouvelles intégrations
- Changements de politiques

Les changements normaux nécessitent une évaluation d'impact, un examen de sécurité et l'approbation du CCC.

### 11.2.3 Changements d'urgence

Changements urgents requis pour restaurer le service ou traiter des incidents de sécurité :
- Remédiation des vulnérabilités de sécurité
- Actions d'intervention en cas d'incident
- Restauration critique du service

Les changements d'urgence peuvent contourner l'approbation normale avec un examen rétrospectif.

## 11.3 Processus de changement

### 11.3.1 Demande

1. Le demandeur de changement crée une demande de changement
2. La demande inclut :
   - Description du changement
   - Justification commerciale
   - Plan de mise en œuvre technique
   - Évaluation d'impact
   - Plan de retour arrière
   - Plan de test
   - Calendrier de mise en œuvre

### 11.3.2 Évaluation

1. Examen technique du plan de mise en œuvre
2. Examen de sécurité pour les changements liés à la sécurité
3. Évaluation d'impact sur la plateforme et les clients
4. Évaluation des risques
5. Validation du plan de retour arrière

### 11.3.3 Approbation

**Changements standards**
- Pré-approuvés par catégorie
- L'équipe de mise en œuvre exécute

**Changements normaux**
- Examen du Comité consultatif des changements
- Approbation de l'autorité de sécurité pour les changements de sécurité
- Fenêtre de mise en œuvre planifiée

**Changements d'urgence**
- Approbation verbale du gestionnaire de la plateforme
- Examen rétrospectif du CCC

### 11.3.4 Mise en œuvre

1. Vérification pré-mise en œuvre
2. Mise en œuvre selon le plan approuvé
3. Surveillance de la progression
4. Escalade des problèmes si requis
5. Retour arrière si les critères de succès ne sont pas atteints

### 11.3.5 Vérification

1. Tests fonctionnels
2. Vérification de sécurité
3. Vérification de performance
4. Vérification de l'impact client
5. Mise à jour de la documentation

### 11.3.6 Clôture

1. Enregistrement de changement mis à jour
2. Leçons apprises documentées
3. Référence de configuration mise à jour
4. Parties prenantes notifiées

## 11.4 Pipeline CI/CD

### 11.4.1 Structure du pipeline

Les déploiements de la plateforme DOIVENT utiliser des pipelines CI/CD :

**Intégration continue**
- La validation du code déclenche la construction
- Linting et validation automatisés
- Analyse de sécurité (identifiants, vulnérabilités)
- Génération du plan Terraform
- Porte de révision et d'approbation du plan

**Déploiement continu**
- Les changements approuvés sont déployés automatiquement
- Déploiement par étapes (dev → préproduction → prod)
- Tests de fumée automatisés
- Retour arrière automatique en cas d'échec

### 11.4.2 Sécurité du pipeline

Les pipelines CI/CD DOIVENT mettre en œuvre :

a) Principal de service avec moindre privilège
b) Secrets stockés dans Key Vault ou secrets du pipeline
c) Portes d'approbation pour les déploiements en production
d) Journalisation d'audit des exécutions du pipeline
e) Pas d'identifiants codés en dur dans le code

### 11.4.3 Fenêtres de déploiement

Les changements de la plateforme DOIVENT être déployés pendant les fenêtres approuvées :

- **Fenêtre standard :** Mardi-jeudi, 06h00-08h00 HE
- **Fenêtre d'urgence :** Au besoin avec approbation
- **Périodes de gel :** Annoncées à l'avance pour les périodes commerciales critiques

---

# 12. AUDIT ET RESPONSABILISATION

## 12.1 Aperçu

L'audit et la responsabilisation assurent une journalisation, une surveillance et une rétention complètes des événements pertinents pour la sécurité aux fins de détection, d'enquête et de conformité.

**Familles de contrôles ITSG-33 :** AU (Audit et responsabilisation)

## 12.2 Architecture de journalisation

### 12.2.1 Log Analytics central

Tous les journaux de la plateforme DOIVENT être collectés dans un espace de travail Log Analytics central :

a) L'abonnement de la plateforme héberge Log Analytics
b) Toutes les ressources de la plateforme envoient des diagnostics
c) Les spokes clients envoient des diagnostics
d) Rétention configurée selon les exigences
e) Accès contrôlé via RBAC

### 12.2.2 Sources de journaux

Les sources de journaux suivantes DOIVENT être collectées :

**Journaux d'activité Azure**
- Opérations du plan de contrôle
- Actions administratives
- Événements d'état du service

**Journaux de connexion Azure AD**
- Événements d'authentification des utilisateurs
- Résultats d'accès conditionnel
- Événements AMF

**Journaux d'audit Azure AD**
- Changements au répertoire
- Changements aux applications
- Changements d'appartenance aux groupes

**Journaux de diagnostic des ressources**
- Journaux du pare-feu Azure
- Journaux d'accès à Key Vault
- Journaux d'accès au stockage
- Journaux des machines virtuelles
- Journaux de flux réseau

**Journaux de sécurité**
- Alertes de Defender pour le cloud
- Incidents Sentinel
- Constatations de vulnérabilités

### 12.2.3 Format des journaux

Les journaux DOIVENT inclure :

a) Horodatage (UTC)
b) Type d'événement
c) Identité de l'acteur
d) Adresse IP source
e) Ressource affectée
f) Action effectuée
g) Résultat (succès/échec)

## 12.3 Microsoft Sentinel

### 12.3.1 Mise en œuvre du SIEM

Microsoft Sentinel DOIT être déployé pour la surveillance de la sécurité :

a) Connecté à l'espace de travail Log Analytics
b) Connecteurs de données activés pour toutes les sources pertinentes
c) Règles d'analyse pour la détection des menaces
d) Playbooks de réponse automatisée
e) Flux de travail de gestion des incidents

### 12.3.2 Règles de détection

Sentinel DOIT inclure des règles de détection pour :

**Menaces d'identité**
- Tentatives de force brute
- Emplacements de connexion suspects
- Voyage impossible
- Utilisation de comptes privilégiés
- Abus de principaux de service

**Menaces réseau**
- Modèles de refus du pare-feu
- Trafic de commande et contrôle
- Indicateurs d'exfiltration de données
- Mouvement latéral

**Menaces aux ressources**
- Création de ressources non autorisée
- Changements de configuration
- Accès aux clés de chiffrement
- Suppression de sauvegardes

### 12.3.3 Gestion des incidents

Les incidents Sentinel DOIVENT être gérés :

a) Affectation de l'incident dans les 15 minutes
b) Triage initial dans l'heure
c) Procédures d'enquête suivies
d) Escalade selon la gravité de l'incident
e) Documentation de l'incident maintenue

## 12.4 Rétention des journaux

### 12.4.1 Exigences de rétention

La rétention des journaux DOIT respecter les minimums suivants :

| Type de journal | Rétention en ligne | Rétention en archive |
|-----------------|-------------------|----------------------|
| Journaux de sécurité | 365 jours | 7 ans |
| Journaux d'activité | 365 jours | 7 ans |
| Journaux d'authentification | 365 jours | 7 ans |
| Journaux du pare-feu | 90 jours | 1 an |
| Diagnostics des ressources | 90 jours | 1 an |

### 12.4.2 Archive des journaux

Les journaux au-delà de la rétention en ligne DOIVENT être :

a) Exportés vers un stockage sécurisé
b) Chiffrés au repos
c) Accès contrôlé
d) Intégrité protégée
e) Récupérables pour enquête

## 12.5 Surveillance et alertes

### 12.5.1 Catégories d'alertes

Les alertes DOIVENT être configurées pour :

**Critique (réponse immédiate)**
- Incident de sécurité détecté
- Service d'authentification dégradé
- Défaillance du pare-feu
- Utilisation d'un compte d'urgence

**Élevé (réponse dans l'heure)**
- Échecs d'authentification multiples
- Activation de rôle privilégié
- Violation de politique de sécurité
- Dérive de configuration détectée

**Moyen (réponse dans les 4 heures)**
- Vulnérabilité détectée
- Écart de conformité
- Seuil de capacité dépassé

**Faible (réponse dans les 24 heures)**
- Événements de sécurité informatifs
- Avertissements opérationnels

### 12.5.2 Notification des alertes

Les alertes DOIVENT être acheminées vers :

a) Centre des opérations de sécurité (toutes les alertes de sécurité)
b) Opérations de la plateforme (alertes opérationnelles)
c) Personnel de garde (alertes critiques)
d) Direction (incidents de sécurité critiques)

---

# 13. INTERVENTION EN CAS D'INCIDENT

## 13.1 Aperçu

L'intervention en cas d'incident fournit des procédures structurées pour détecter, répondre, contenir et récupérer des incidents de sécurité affectant la plateforme.

**Familles de contrôles ITSG-33 :** IR (Intervention en cas d'incident)

## 13.2 Classification des incidents

### 13.2.1 Niveaux de gravité

| Gravité | Description | Temps de réponse | Exemples |
|---------|-------------|------------------|----------|
| Critique | Violation active, exposition importante de données, compromission de la plateforme | Immédiat | Violation de données confirmée, rançongiciel, compromission de compte admin de plateforme |
| Élevé | Violation probable, vulnérabilité importante, impact majeur sur le service | 1 heure | Escalade de privilèges réussie, vulnérabilité zero-day, contournement d'authentification |
| Moyen | Problème de sécurité potentiel, incident contenu | 4 heures | Succès d'hameçonnage (contenu), violation de politique, tentatives d'attaque échouées |
| Faible | Événement de sécurité mineur, informatif | 24 heures | Divulgation de vulnérabilité, activité suspecte (non confirmée) |

### 13.2.2 Catégories d'incidents

- **Accès non autorisé :** Accès non autorisé réussi ou tenté
- **Logiciel malveillant :** Détection de logiciel malveillant
- **Violation de données :** Exposition de données confirmée ou suspectée
- **Déni de service :** Attaques de perturbation de service
- **Incident de configuration :** Mauvaise configuration de sécurité découverte
- **Violation de politique :** Violation des politiques de sécurité

## 13.3 Phases d'intervention en cas d'incident

### 13.3.1 Détection

Les incidents peuvent être détectés par :

a) Alertes Microsoft Sentinel
b) Alertes Defender pour le cloud
c) Rapports d'utilisateurs
d) Notifications de tiers
e) Renseignements sur les menaces
f) Surveillance automatisée

### 13.3.2 Triage

Lors de la détection :

1. Valider l'incident (confirmation de vrai positif)
2. Classer la gravité et la catégorie
3. Affecter le propriétaire de l'incident
4. Notifier les parties concernées
5. Commencer la documentation

### 13.3.3 Confinement

Actions de confinement selon le type d'incident :

**Compromission de compte**
- Désactiver les comptes affectés
- Révoquer les sessions actives
- Réinitialiser les identifiants
- Examiner l'activité du compte

**Incident réseau**
- Isoler les ressources affectées
- Bloquer les IP/domaines malveillants
- Capturer le trafic réseau pour analyse

**Logiciel malveillant**
- Isoler les systèmes affectés
- Préserver les preuves
- Bloquer les indicateurs de compromission

**Violation de données**
- Identifier les données affectées
- Préserver les journaux d'accès
- Évaluer la portée de l'exposition

### 13.3.4 Éradication

Supprimer la menace :

a) Supprimer les artéfacts malveillants
b) Fermer la vulnérabilité exploitée
c) Corriger les systèmes affectés
d) Renforcer les contrôles

### 13.3.5 Récupération

Restaurer les opérations normales :

a) Restaurer à partir de sauvegardes propres si requis
b) Vérifier l'intégrité du système
c) Surveiller la récurrence
d) Restauration progressive du service

### 13.3.6 Post-incident

Après la clôture de l'incident :

a) Compléter la documentation de l'incident
b) Mener une revue des leçons apprises
c) Mettre à jour les procédures au besoin
d) Mettre en œuvre des contrôles supplémentaires
e) Rapporter aux organes de gouvernance

## 13.4 Équipe d'intervention en cas d'incident

### 13.4.1 Structure de l'équipe

| Rôle | Responsabilités |
|------|-----------------|
| Commandant d'incident | Coordination globale de l'incident |
| Analyste de sécurité | Enquête technique |
| Ingénieur de plateforme | Actions de remédiation de la plateforme |
| Responsable des communications | Communication avec les parties prenantes |
| Juridique/Vie privée (au besoin) | Orientation juridique et vie privée |

### 13.4.2 Escalade

| Gravité | Notification |
|---------|-------------|
| Critique | Direction, Juridique, Client (si affecté), CCCS (si requis) |
| Élevé | Autorité de sécurité, Gestionnaire de plateforme |
| Moyen | Gestionnaire des opérations de sécurité |
| Faible | Équipe d'analystes de sécurité |

## 13.5 Communication

### 13.5.1 Communication interne

a) Canaux de communication sécurisés (Teams, courriel chiffré)
b) Mises à jour de l'état à intervalles définis
c) Partage d'information selon le besoin de savoir

### 13.5.2 Communication externe

a) Notification aux clients selon les procédures convenues
b) Notification réglementaire comme requis
c) Communication publique uniquement par les canaux approuvés
d) Pas de discussion des incidents sur les médias sociaux

### 13.5.3 Exigences de déclaration

Les incidents impliquant des données Protégé B DOIVENT être signalés à :

a) Autorité de sécurité organisationnelle
b) Responsable de la vie privée (si des renseignements personnels sont impliqués)
c) CCCS (incidents cybernétiques importants)
d) Clients affectés

---

# 14. PLANIFICATION DE LA CONTINUITÉ

## 14.1 Aperçu

La planification de la continuité assure la résilience et la capacité de reprise de la plateforme par des procédures de sauvegarde, de reprise après sinistre et de continuité des activités.

**Familles de contrôles ITSG-33 :** CP (Planification de la continuité)

## 14.2 Objectifs de reprise

### 14.2.1 Objectifs de reprise de la plateforme

| Composant | OTR | OPR |
|-----------|-----|-----|
| Services d'identité | 1 heure | 0 (aucune perte de données) |
| Connectivité réseau | 2 heures | S.O. |
| Surveillance de sécurité | 4 heures | 1 heure |
| Services de gestion | 4 heures | 24 heures |
| Configuration de la plateforme | 4 heures | 24 heures |

### 14.2.2 Objectifs de reprise des clients

Les objectifs de reprise des charges de travail clients sont définis par entente de service client. La plateforme fournit la capacité d'infrastructure; le client est responsable de la reprise de la charge de travail.

## 14.3 Sauvegarde

### 14.3.1 Portée de la sauvegarde

Les sauvegardes de la plateforme DOIVENT inclure :

a) **Sauvegardes de configuration**
   - Dépôt IaC (Git)
   - Définitions Azure Policy
   - Affectations RBAC
   - Règles de pare-feu
   - Paramètres de diagnostic

b) **Sauvegardes de données**
   - Key Vault (clés et secrets)
   - Données Log Analytics (via exportation)
   - Configuration Azure AD

c) **Responsabilité du client**
   - Sauvegardes de machines virtuelles
   - Sauvegardes de bases de données
   - Données d'application

### 14.3.2 Procédures de sauvegarde

**Dépôt IaC**
- Répliqué vers un emplacement secondaire
- Récupération ponctuelle disponible
- Historique minimum de 90 jours

**Key Vault**
- Suppression réversible activée (90 jours)
- Protection contre le vidage activée
- Exportation des clés pour les clés critiques

**Azure AD**
- Réplication gérée par Microsoft
- Suppression réversible pour les utilisateurs (30 jours)
- Configuration documentée pour la recréation

### 14.3.3 Vérification des sauvegardes

La vérification des sauvegardes DOIT être effectuée :

a) Vérification mensuelle de l'exhaustivité des sauvegardes
b) Restauration test trimestrielle des composants critiques
c) Test de récupération complet annuel

## 14.4 Reprise après sinistre

### 14.4.1 Stratégie de RS

La plateforme emploie les stratégies de RS suivantes :

**Actif-passif**
- Principal : Canada Centre
- Secondaire : Canada Est
- Basculement manuel pour les services de plateforme

**Récupération de configuration**
- L'IaC permet une reconstruction rapide
- Procédures de récupération documentées
- Runbooks de récupération testés

### 14.4.2 Procédures de basculement

Le basculement DOIT être initié lorsque :

a) Panne régionale Azure déclarée
b) Le temps de récupération dépasse le seuil acceptable
c) Un incident de sécurité nécessite l'isolement

Procédures de basculement :

1. Le commandant d'incident déclare l'événement de RS
2. Évaluation de l'état actuel
3. Décision de basculement
4. Exécution du runbook de basculement
5. Vérification de la fonctionnalité de la plateforme
6. Notification des clients
7. Surveillance de la région secondaire

### 14.4.3 Procédures de retour arrière

Retour arrière vers la région principale :

1. Région principale restaurée et vérifiée
2. Synchronisation des données vérifiée
3. Fenêtre de retour arrière planifiée
4. Exécution du runbook de retour arrière
5. Vérification de la fonctionnalité de la plateforme
6. Notification des clients

## 14.5 Continuité des activités

### 14.5.1 Scénarios de continuité

Les scénarios suivants sont traités :

a) Panne régionale Azure
b) Indisponibilité du personnel clé
c) Incident de sécurité nécessitant l'isolement
d) Interruption du service fournisseur

### 14.5.2 Continuité du personnel

Continuité des opérations de la plateforme :

a) Formation croisée du personnel
b) Procédures documentées
c) Rotation de garde
d) Contrats de support fournisseur

### 14.5.3 Tests

Les tests de continuité DOIVENT inclure :

a) Exercice sur table annuel
b) Test de basculement annuel
c) Vérification trimestrielle des sauvegardes
d) Documentation des leçons apprises

---

# 15. GESTION DES VULNÉRABILITÉS

## 15.1 Aperçu

La gestion des vulnérabilités fournit l'identification systématique, l'évaluation et la remédiation des vulnérabilités de sécurité dans les composants de la plateforme.

**Familles de contrôles ITSG-33 :** RA (Évaluation des risques), SI (Intégrité des systèmes)

## 15.2 Identification des vulnérabilités

### 15.2.1 Analyse

L'analyse des vulnérabilités DOIT être effectuée :

**Microsoft Defender pour le cloud**
- Évaluation continue des ressources Azure
- Analyse de conformité de la configuration
- Analyse sans agent lorsque pris en charge

**Microsoft Defender pour les serveurs**
- Analyse des vulnérabilités basée sur agent
- Vulnérabilités du système d'exploitation
- Vulnérabilités des logiciels installés

**Gestion des vulnérabilités Microsoft Defender**
- Inventaire logiciel
- Priorisation des vulnérabilités
- Suivi de la remédiation

### 15.2.2 Renseignements sur les menaces

Les sources de renseignements sur les menaces DOIVENT inclure :

a) Renseignements sur les menaces Microsoft
b) Alertes et avis du CCCS
c) Bulletins de sécurité des fournisseurs
d) Bases de données CVE

## 15.3 Évaluation des vulnérabilités

### 15.3.1 Cote de gravité

Les vulnérabilités DOIVENT être cotées selon les scores CVSS v3 :

| Score CVSS | Gravité | Délai de remédiation |
|------------|---------|---------------------|
| 9,0-10,0 | Critique | 72 heures |
| 7,0-8,9 | Élevé | 7 jours |
| 4,0-6,9 | Moyen | 30 jours |
| 0,1-3,9 | Faible | 90 jours |

### 15.3.2 Évaluation des risques

L'évaluation des risques de vulnérabilité DOIT considérer :

a) Score CVSS
b) Exploitabilité (exploit public disponible?)
c) Criticité de l'actif
d) Exposition (orienté Internet?)
e) Contrôles compensatoires

## 15.4 Remédiation

### 15.4.1 Processus de remédiation

1. Vulnérabilité identifiée et évaluée
2. Cote de risque attribuée
3. Propriétaire de la remédiation attribué
4. Remédiation planifiée
5. Demande de changement soumise
6. Remédiation mise en œuvre
7. Vérification effectuée
8. Vulnérabilité clôturée

### 15.4.2 Méthodes de remédiation

**Correction**
- Correctifs du système d'exploitation
- Correctifs d'application
- Mises à jour de micrologiciel

**Configuration**
- Durcissement de sécurité
- Désactivation des fonctionnalités vulnérables
- Isolation réseau

**Contrôles compensatoires**
- Règles WAF
- Règles de pare-feu
- Surveillance renforcée

### 15.4.3 Exceptions

Exceptions de remédiation de vulnérabilités :

a) Doivent être documentées avec justification commerciale
b) Contrôles compensatoires documentés
c) Date d'expiration de l'exception définie
d) Approbation de l'autorité de sécurité requise
e) Examen régulier des exceptions

## 15.5 Gestion des correctifs

### 15.5.1 Sources de correctifs

Composants de la plateforme corrigés par :

**Azure PaaS**
- Correction gérée par Microsoft
- L'équipe de la plateforme surveille les annonces

**VM de la plateforme**
- Azure Update Management
- Correction automatisée activée
- Fenêtres de maintenance définies

**Charges de travail clients**
- Responsabilité du client
- La plateforme fournit la capacité Update Management

### 15.5.2 Calendrier de correction

| Catégorie de correctif | Calendrier |
|------------------------|------------|
| Sécurité critique | Dans les 72 heures |
| Sécurité élevée | Dans les 7 jours |
| Autre sécurité | Fenêtre de maintenance mensuelle |
| Mises à jour de fonctionnalités | Trimestriel (testé d'abord) |

### 15.5.3 Test des correctifs

Les correctifs DOIVENT être testés :

a) Environnement hors production d'abord
b) Tests automatisés lorsque possible
c) Déploiement échelonné en production
d) Capacité de retour arrière vérifiée

---

# 16. PROTECTION DES DONNÉES

## 16.1 Aperçu

La protection des données assure la manipulation, la protection et la gestion du cycle de vie appropriées des données au sein de la plateforme.

**Familles de contrôles ITSG-33 :** MP (Protection des supports), SC (Protection des systèmes et des communications)

## 16.2 Classification des données

### 16.2.1 Niveaux de classification

La plateforme prend en charge les données classifiées jusqu'à Protégé B :

| Classification | Description |
|----------------|-------------|
| Protégé B | Information dont la compromission pourrait causer un préjudice grave |
| Protégé A | Information dont la compromission pourrait causer un préjudice |
| Non classifié | Information approuvée pour diffusion publique |

### 16.2.2 Responsabilité de classification

La classification des données est la responsabilité du propriétaire des données (client). La plateforme fournit des contrôles appropriés pour Protégé B.

## 16.3 Traitement des données

### 16.3.1 Données au repos

Les données Protégé B au repos DOIVENT être :

a) Chiffrées à l'aide d'AES-256 ou équivalent
b) Stockées uniquement dans les régions canadiennes
c) Accès contrôlé via RBAC
d) Sauvegardées selon les exigences de rétention

### 16.3.2 Données en transit

Les données Protégé B en transit DOIVENT être :

a) Chiffrées à l'aide de TLS 1.2 ou supérieur
b) Non transmises sur des réseaux non fiables sans chiffrement
c) Non transmises hors du Canada sans autorisation

### 16.3.3 Données en cours d'utilisation

Les données Protégé B en cours d'utilisation DOIVENT être :

a) Accessibles uniquement par le personnel autorisé
b) Protégées contre la visualisation non autorisée
c) Non copiées vers des emplacements non autorisés

## 16.4 Résidence des données

### 16.4.1 Restrictions géographiques

Toutes les données de la plateforme DOIVENT résider au Canada :

a) Régions Azure : Canada Centre, Canada Est uniquement
b) Pas de réplication vers des régions non canadiennes
c) Azure Policy applique la restriction régionale
d) Les données clients restent au Canada

### 16.4.2 Souveraineté des données

Les données restent sous la juridiction canadienne :

a) Opérations du centre de données Microsoft Canada
b) Le droit canadien s'applique
c) Soumis uniquement aux ordonnances judiciaires canadiennes légales

## 16.5 Cycle de vie des données

### 16.5.1 Rétention

La rétention des données DOIT être conforme aux :

a) Calendriers de rétention applicables
b) Exigences de conservation légale
c) Rétention minimale pour la conformité (varie selon le type de données)
d) Rétention maximale pour limiter l'exposition

### 16.5.2 Élimination

L'élimination des données DOIT assurer :

a) Suppression sécurisée utilisant les capacités Azure
b) Période de suppression réversible avant la suppression permanente
c) Approbation de l'élimination documentée
d) Vérification de l'élimination

### 16.5.3 Assainissement des supports

Pour les supports physiques (le cas échéant) :

a) Microsoft responsable des supports du centre de données
b) Client responsable de tout support physique
c) L'assainissement respecte les normes du CCCS

---

# 17. SURVEILLANCE CONTINUE

## 17.1 Aperçu

La surveillance continue maintient une connaissance continue de la posture de sécurité, des menaces et des vulnérabilités par l'évaluation automatisée et manuelle.

**Familles de contrôles ITSG-33 :** CA (Évaluation de sécurité), PM (Gestion de programme)

## 17.2 Stratégie de surveillance

### 17.2.1 Objectifs

La surveillance continue DOIT :

a) Maintenir la connaissance de la posture de sécurité
b) Détecter les événements et incidents de sécurité
c) Identifier la dérive de configuration
d) Suivre l'état des vulnérabilités
e) Vérifier l'efficacité des contrôles

### 17.2.2 Domaines de surveillance

| Domaine | Outils | Fréquence |
|---------|--------|-----------|
| Posture de sécurité | Defender pour le cloud | Continue |
| Détection des menaces | Microsoft Sentinel | Continue |
| Conformité | Azure Policy | Continue |
| Vulnérabilité | Gestion des vulnérabilités Defender | Quotidienne |
| Configuration | État Terraform | Continue |
| Accès | Journaux Azure AD | Continue |

## 17.3 Gestion de la posture de sécurité

### 17.3.1 Defender pour le cloud

Microsoft Defender pour le cloud DOIT :

a) Être activé sur tous les abonnements
b) Fonctionnalités de sécurité améliorées activées
c) Score de sécurité surveillé
d) Recommandations examinées hebdomadairement
e) Conformité réglementaire suivie

### 17.3.2 Score de sécurité

La plateforme DOIT maintenir un score de sécurité minimum :

a) Cible : 80 % ou plus
b) Examen hebdomadaire des changements de score
c) Plan d'action pour l'amélioration du score
d) Score rapporté à la gouvernance

### 17.3.3 Tableau de bord de conformité

La conformité réglementaire DOIT être suivie :

a) Contrôles PBMM du CCCS mappés
b) État de conformité surveillé
c) Non-conformité enquêtée
d) Exemptions documentées

## 17.4 Détection des menaces

### 17.4.1 Capacités de détection

La détection des menaces DOIT inclure :

a) Détection des menaces d'identité (Azure AD Identity Protection)
b) Détection des menaces réseau (Pare-feu Azure, Sentinel)
c) Détection des menaces de point de terminaison (Defender pour point de terminaison)
d) Détection des menaces de charge de travail infonuagique (Defender pour le cloud)

### 17.4.2 Gestion des alertes

Les alertes de sécurité DOIVENT être :

a) Triées dans le délai de service
b) Enquêtées selon les procédures documentées
c) Escaladées selon la gravité
d) Documentées dans le suivi des incidents

## 17.5 Indicateurs et rapports

### 17.5.1 Indicateurs de sécurité

Les indicateurs suivants DOIVENT être suivis :

| Indicateur | Cible | Fréquence |
|------------|-------|-----------|
| Score de sécurité | ≥80 % | Hebdomadaire |
| Vulnérabilités critiques | 0 ouverte >72h | Quotidienne |
| Vulnérabilités élevées | 0 ouverte >7 jours | Hebdomadaire |
| Couverture AMF | 100 % | Mensuelle |
| Examens d'accès privilégié | 100 % complétés | Mensuelle |
| Incidents de sécurité | Tendance à la baisse | Mensuelle |
| Temps moyen de détection | <1 heure | Mensuelle |
| Temps moyen de réponse | <4 heures | Mensuelle |

### 17.5.2 Rapports

Les rapports de sécurité DOIVENT être produits :

**Hebdomadaire**
- Résumé des opérations de sécurité
- Résumé des alertes et incidents
- État des vulnérabilités

**Mensuel**
- Rapport de posture de sécurité
- État de conformité
- Tableau de bord des indicateurs
- Mise à jour du registre des risques

**Trimestriel**
- Rapport de sécurité exécutif
- Analyse des tendances
- Évaluation de l'efficacité des contrôles

**Annuel**
- Revue du programme de sécurité
- Mise à jour de l'évaluation des risques
- Revue des politiques et procédures

---

# 18. EXPLOITATION DE LA PLATEFORME

## 18.1 Aperçu

L'exploitation de la plateforme définit les procédures opérationnelles quotidiennes pour maintenir le fonctionnement sécurisé et fiable de la plateforme de zone d'atterrissage Azure.

## 18.2 Procédures opérationnelles

### 18.2.1 Opérations quotidiennes

**Opérations de sécurité**
- Examiner les incidents Sentinel
- Examiner les alertes Defender pour le cloud
- Examiner les anomalies d'authentification
- Traiter les demandes d'accès

**Opérations de la plateforme**
- Examiner la santé de la plateforme
- Examiner les indicateurs de capacité
- Traiter les demandes de changement
- Traiter les problèmes opérationnels

### 18.2.2 Opérations hebdomadaires

- Examiner le score de posture de sécurité
- Examiner l'état des vulnérabilités
- Examiner la conformité aux politiques
- Tenir la réunion du CCC
- Examiner les incidents ouverts

### 18.2.3 Opérations mensuelles

- Examens d'accès pour les rôles privilégiés
- Rapports des indicateurs de sécurité
- Examen de la planification de la capacité
- Revue et mises à jour des procédures

### 18.2.4 Opérations trimestrielles

- Revue du registre des risques
- Évaluation de la conformité
- Exercices sur table
- Formation et sensibilisation

### 18.2.5 Opérations annuelles

- Revue des politiques et procédures
- Évaluation de sécurité
- Test de reprise après sinistre
- Revue de la continuité des activités

## 18.3 Maintenance

### 18.3.1 Fenêtres de maintenance

Maintenance planifiée :

- **Standard :** Mardi-jeudi, 06h00-08h00 HE
- **Étendue :** Premier samedi du mois, 02h00-06h00 HE
- **Urgence :** Au besoin avec notification

### 18.3.2 Activités de maintenance

Les activités de maintenance incluent :

a) Correction de sécurité
b) Mises à jour de configuration
c) Ajustements de capacité
d) Renouvellements de certificats
e) Rotations de clés

### 18.3.3 Communication de maintenance

La maintenance DOIT être communiquée :

a) Planifiée : 5 jours ouvrables de préavis
b) Urgence : Dès que possible
c) Post-maintenance : Notification d'achèvement

## 18.4 Gestion de la capacité

### 18.4.1 Surveillance de la capacité

La capacité de la plateforme DOIT être surveillée :

a) Indicateurs Azure Monitor
b) Capacité de l'espace de travail Log Analytics
c) Utilisation de la bande passante réseau
d) Limites de transactions Key Vault

### 18.4.2 Planification de la capacité

La planification de la capacité DOIT inclure :

a) Revue mensuelle de la capacité
b) Évaluation d'impact de l'intégration des clients
c) Projections de croissance
d) Alignement budgétaire

---

# 19. SÉCURITÉ DE L'INTÉGRATION DES CLIENTS

## 19.1 Aperçu

La sécurité de l'intégration des clients assure une posture de sécurité cohérente pour les nouvelles charges de travail clients déployées sur la plateforme.

## 19.2 Processus d'intégration

### 19.2.1 Exigences de sécurité

Avant l'intégration, les clients DOIVENT :

a) Compléter le questionnaire des exigences de sécurité
b) Identifier les exigences de classification des données
c) Identifier les exigences de conformité
d) Désigner un contact de sécurité
e) Reconnaître le modèle de responsabilité partagée

### 19.2.2 Évaluation de sécurité

L'équipe de la plateforme DOIT évaluer :

a) Les exigences de sécurité de la charge de travail client
b) La compatibilité avec les contrôles de sécurité de la plateforme
c) Les contrôles supplémentaires requis
d) Le risque de l'intégration

### 19.2.3 Liste de contrôle d'intégration

Liste de contrôle de sécurité d'intégration :

- [ ] Exigences de sécurité documentées
- [ ] Classification des données confirmée
- [ ] Exigences de conformité confirmées
- [ ] Responsabilité partagée reconnue
- [ ] Contact de sécurité client identifié
- [ ] Abonnement spoke provisionné
- [ ] Segmentation réseau configurée
- [ ] Journalisation configurée
- [ ] Accès provisionné
- [ ] Séance d'information sécurité client complétée

## 19.3 Sécurité des spokes

### 19.3.1 Référence des spokes

Chaque spoke client DOIT avoir :

a) Héritage d'Azure Policy du groupe de gestion des zones d'atterrissage
b) Appairage réseau au hub
c) Tunnelisation forcée via le pare-feu Azure
d) Paramètres de diagnostic vers Log Analytics central
e) Defender pour le cloud activé
f) NSG par défaut sur les sous-réseaux

### 19.3.2 Responsabilités des clients

Les clients sont responsables de :

a) Configuration de la sécurité des charges de travail
b) Sécurité des applications
c) Protection des données au sein de la charge de travail
d) Gestion des vulnérabilités des charges de travail
e) Sauvegarde des charges de travail
f) Gestion des accès aux charges de travail

## 19.4 Retrait

### 19.4.1 Processus de retrait

Le retrait des clients DOIT inclure :

a) Assistance à l'exportation/migration des données
b) Révocation des accès
c) Vérification de la suppression des ressources
d) Rétention des journaux selon les exigences
e) Mise hors service de l'abonnement

### 19.4.2 Traitement des données

Lors du retrait :

a) Données clients exportées selon les exigences du client
b) Rétention des données selon les exigences légales
c) Suppression sécurisée après la période de rétention
d) Confirmation de suppression fournie

---

# 20. RÔLES ET RESPONSABILITÉS

## 20.1 Matrice RACI

| Activité | Autorité de sécurité | Équipe de plateforme | Opérations de sécurité | Client |
|----------|---------------------|----------------------|------------------------|--------|
| Gouvernance de la sécurité | A | R | C | I |
| Acceptation des risques | A | R | C | I |
| Gestion des politiques | A | R | C | I |
| Gestion des identités | A | R | R | C |
| Sécurité réseau | A | R | C | I |
| Surveillance de la sécurité | I | C | R | I |
| Intervention en cas d'incident | A | R | R | C |
| Gestion des vulnérabilités | A | R | R | C |
| Gestion des changements | A | R | C | C |
| Intégration des clients | A | R | C | R |
| Sécurité des charges de travail | I | C | C | R |
| Protection des données | I | C | C | R |

**Légende :** R=Responsable, A=Imputable, C=Consulté, I=Informé

## 20.2 Définitions des rôles

### 20.2.1 Autorité de sécurité

- Imputable de la posture de sécurité de la plateforme
- Approuve les politiques et exceptions de sécurité
- Accepte le risque résiduel
- Commande les évaluations de sécurité

### 20.2.2 Autorité de sécurité de la plateforme

- Gouvernance quotidienne de la sécurité
- Supervision de la mise en œuvre des contrôles de sécurité
- Supervision de la gestion des incidents de sécurité
- Surveillance continue de la conformité

### 20.2.3 Ingénierie de la plateforme

- Déploiement de l'infrastructure de la plateforme
- Gestion de la configuration
- Mise en œuvre des changements
- Gestion de la capacité

### 20.2.4 Opérations de sécurité

- Surveillance et alertes de sécurité
- Détection et intervention en cas d'incident
- Gestion des vulnérabilités
- Administration des outils de sécurité

### 20.2.5 Opérations de la plateforme

- Surveillance de la santé de la plateforme
- Résolution des problèmes opérationnels
- Exécution de la maintenance
- Support aux clients

### 20.2.6 Contact de sécurité client

- Responsabilité de la sécurité des charges de travail
- Coordination des incidents avec la plateforme
- Gestion des demandes d'accès
- Coordination de la conformité

---

# 21. GESTION DES EXCEPTIONS

## 21.1 Processus d'exception

### 21.1.1 Demande d'exception

Les exceptions de sécurité nécessitent :

a) Justification commerciale
b) Évaluation des risques
c) Contrôles compensatoires
d) Durée de l'exception
e) Calendrier de révision

### 21.1.2 Approbation d'exception

| Niveau de risque | Autorité d'approbation |
|------------------|------------------------|
| Faible | Autorité de sécurité de la plateforme |
| Moyen | Autorité de sécurité |
| Élevé | Direction + Autorité de sécurité |
| Critique | Non permis |

### 21.1.3 Documentation d'exception

Les exceptions DOIVENT être documentées avec :

- ID d'exception
- Description
- Justification
- Évaluation des risques
- Contrôles compensatoires
- Approbation
- Date d'expiration
- Calendrier de révision

## 21.2 Révision des exceptions

Les exceptions DOIVENT être révisées :

a) Avant l'expiration
b) Après les incidents de sécurité
c) Après les changements importants
d) Au moins annuellement

---

# 22. VÉRIFICATION DE LA CONFORMITÉ

## 22.1 Activités de conformité

### 22.1.1 Conformité continue

- Surveillance de la conformité Azure Policy
- Conformité réglementaire Defender pour le cloud
- Validation automatisée des contrôles
- Détection de la dérive de configuration

### 22.1.2 Évaluation périodique

- Revues de conformité trimestrielles
- Évaluations de sécurité annuelles
- Tests d'intrusion (annuels)
- Audits par des tiers (au besoin)

## 22.2 Gestion des preuves

### 22.2.1 Collecte des preuves

Les preuves DOIVENT être maintenues pour :

- Mise en œuvre des contrôles
- Conformité aux politiques
- Intervention en cas d'incident
- Gestion des changements
- Gestion des accès

### 22.2.2 Rétention des preuves

Les preuves DOIVENT être conservées :

- Minimum 3 ans
- Plus longtemps selon les exigences spécifiques
- Accessibles pour les audits

---

# 23. MAINTENANCE DU DOCUMENT

## 23.1 Calendrier de révision

Ce document DOIT être révisé :

- Annuellement (minimum)
- À la suite de changements importants
- À la suite d'incidents de sécurité
- À la suite de constatations d'audit

## 23.2 Processus de changement

Les changements au document nécessitent :

a) Demande de changement avec justification
b) Révision par l'autorité de sécurité
c) Révision par les parties prenantes
d) Approbation
e) Mise à jour de la version
f) Communication aux parties prenantes

## 23.3 Contrôle de version

Toutes les versions DOIVENT être maintenues avec :

- Numéro de version
- Date
- Auteur
- Description du changement
- Approbation

---

# ANNEXE A : CORRESPONDANCE DES CONTRÔLES ITSG-33

## A.1 Résumé de la mise en œuvre des contrôles

| Famille | Contrôle | Mise en œuvre | État |
|---------|----------|---------------|------|
| **AC - Contrôle d'accès** ||||
| AC-1 | Politique de contrôle d'accès | Ce document + procédures | Mis en œuvre |
| AC-2 | Gestion des comptes | Entra ID + procédures | Mis en œuvre |
| AC-3 | Application de l'accès | Azure RBAC | Mis en œuvre |
| AC-4 | Flux d'information | Pare-feu Azure + NSG | Mis en œuvre |
| AC-5 | Séparation des fonctions | Conception des rôles RBAC | Mis en œuvre |
| AC-6 | Moindre privilège | RBAC + PIM | Mis en œuvre |
| AC-7 | Échec de connexion | Accès conditionnel + surveillance | Mis en œuvre |
| AC-8 | Notification d'utilisation du système | Bannière du portail Azure | Mis en œuvre |
| AC-11 | Verrouillage de session | Contrôles de session d'accès conditionnel | Mis en œuvre |
| AC-12 | Fin de session | Délai de session Azure | Mis en œuvre |
| AC-17 | Accès à distance | Azure Bastion + VPN | Mis en œuvre |
| AC-18 | Accès sans fil | Non applicable (infonuagique) | S.O. |
| AC-19 | Contrôle d'accès mobile | Accès conditionnel | Mis en œuvre |
| AC-20 | Systèmes externes | Contrôle de sortie du pare-feu | Mis en œuvre |
| **AU - Audit et responsabilisation** ||||
| AU-1 | Politique d'audit | Ce document | Mis en œuvre |
| AU-2 | Événements d'audit | Log Analytics + Sentinel | Mis en œuvre |
| AU-3 | Contenu des enregistrements d'audit | Journaux de diagnostic Azure | Mis en œuvre |
| AU-4 | Stockage d'audit | Rétention Log Analytics | Mis en œuvre |
| AU-5 | Réponse aux échecs | Surveillance + alertes | Mis en œuvre |
| AU-6 | Révision d'audit | Procédures du COS | Mis en œuvre |
| AU-7 | Réduction d'audit | Requêtes Log Analytics | Mis en œuvre |
| AU-8 | Horodatages | Heure de la plateforme Azure | Mis en œuvre |
| AU-9 | Protection des informations d'audit | RBAC + stockage immuable | Mis en œuvre |
| AU-11 | Rétention des enregistrements d'audit | 365 jours en ligne + archive | Mis en œuvre |
| AU-12 | Génération d'audit | Diagnostics Azure activés | Mis en œuvre |
| **CM - Gestion de la configuration** ||||
| CM-1 | Politique de configuration | Ce document | Mis en œuvre |
| CM-2 | Configuration de référence | Dépôt IaC | Mis en œuvre |
| CM-3 | Changement de configuration | Processus de gestion des changements | Mis en œuvre |
| CM-4 | Analyse d'impact de sécurité | Évaluation des changements | Mis en œuvre |
| CM-5 | Restrictions d'accès | Pipeline IaC + RBAC | Mis en œuvre |
| CM-6 | Paramètres de configuration | Azure Policy | Mis en œuvre |
| CM-7 | Fonctionnalité minimale | Restrictions de ressources | Mis en œuvre |
| CM-8 | Inventaire du système d'information | Azure Resource Graph | Mis en œuvre |
| CM-9 | Plan de configuration | Ce document | Mis en œuvre |
| CM-10 | Utilisation des logiciels | Restrictions de la place de marché | Mis en œuvre |
| CM-11 | Logiciels installés par l'utilisateur | Restrictions de politique | Mis en œuvre |
| **CP - Planification de la continuité** ||||
| CP-1 | Politique de continuité | Ce document | Mis en œuvre |
| CP-2 | Plan de continuité | Section 14 | Mis en œuvre |
| CP-3 | Formation à la continuité | Exercice annuel | Mis en œuvre |
| CP-4 | Tests de continuité | Test RS annuel | Mis en œuvre |
| CP-6 | Stockage alternatif | Région Canada Est | Mis en œuvre |
| CP-7 | Traitement alternatif | Région Canada Est | Mis en œuvre |
| CP-9 | Sauvegarde du système | Azure Backup + IaC | Mis en œuvre |
| CP-10 | Récupération/Reconstitution | Procédures RS | Mis en œuvre |
| **IA - Identification et authentification** ||||
| IA-1 | Politique I&A | Ce document | Mis en œuvre |
| IA-2 | Identification utilisateur | Entra ID | Mis en œuvre |
| IA-3 | Identification appareil | Accès conditionnel | Mis en œuvre |
| IA-4 | Gestion des identifiants | Cycle de vie Entra ID | Mis en œuvre |
| IA-5 | Gestion des authentifiants | Entra ID + AMF | Mis en œuvre |
| IA-6 | Rétroaction des authentifiants | Portail Azure | Mis en œuvre |
| IA-7 | Authentification cryptographique | Authentification par certificat disponible | Mis en œuvre |
| IA-8 | I&A utilisateurs non organisationnels | B2B avec AMF | Mis en œuvre |
| **IR - Intervention en cas d'incident** ||||
| IR-1 | Politique d'intervention | Ce document | Mis en œuvre |
| IR-2 | Formation à l'intervention | Formation COS | Mis en œuvre |
| IR-3 | Tests d'intervention | Exercice annuel | Mis en œuvre |
| IR-4 | Traitement des incidents | Procédures section 13 | Mis en œuvre |
| IR-5 | Surveillance des incidents | Sentinel | Mis en œuvre |
| IR-6 | Signalement des incidents | Procédures de signalement | Mis en œuvre |
| IR-7 | Assistance aux incidents | Support COS | Mis en œuvre |
| IR-8 | Plan d'intervention | Section 13 | Mis en œuvre |
| **SC - Protection des systèmes et communications** ||||
| SC-1 | Politique SC | Ce document | Mis en œuvre |
| SC-5 | Protection DoS | Azure DDoS + Pare-feu | Mis en œuvre |
| SC-7 | Protection des limites | Pare-feu Azure + NSG | Mis en œuvre |
| SC-8 | Confidentialité des transmissions | TLS 1.2+ | Mis en œuvre |
| SC-12 | Gestion des clés cryptographiques | Key Vault | Mis en œuvre |
| SC-13 | Protection cryptographique | Chiffrement Azure | Mis en œuvre |
| SC-17 | Certificats PKI | Certificats gérés | Mis en œuvre |
| SC-20 | DNS sécurisé | Azure DNS | Mis en œuvre |
| SC-23 | Authenticité des sessions | TLS | Mis en œuvre |
| SC-28 | Protection au repos | Chiffrement Azure | Mis en œuvre |
| **SI - Intégrité des systèmes et de l'information** ||||
| SI-1 | Politique SI | Ce document | Mis en œuvre |
| SI-2 | Remédiation des failles | Gestion des vulnérabilités | Mis en œuvre |
| SI-3 | Protection contre le code malveillant | Defender | Mis en œuvre |
| SI-4 | Surveillance du système | Sentinel + Defender | Mis en œuvre |
| SI-5 | Alertes de sécurité | Avis du CCCS | Mis en œuvre |
| SI-7 | Intégrité des logiciels | Azure Policy | Mis en œuvre |
| SI-10 | Validation des entrées | Responsabilité de l'application | Client |
| SI-12 | Traitement de l'information | Politique de protection des données | Mis en œuvre |

---

# ANNEXE B : EXIGENCES EN MATIÈRE DE PREUVES

## B.1 Matrice des preuves de contrôle

| Domaine de contrôle | Type de preuve | Emplacement | Fréquence |
|---------------------|----------------|-------------|-----------|
| Contrôle d'accès | Exportation RBAC | Portail Azure | Trimestrielle |
| Contrôle d'accès | Journaux d'activation PIM | Azure AD | Continue |
| Contrôle d'accès | Politiques d'accès conditionnel | Azure AD | Trimestrielle |
| Authentification | Rapport d'inscription AMF | Azure AD | Mensuelle |
| Authentification | Journaux de connexion | Log Analytics | Continue |
| Sécurité réseau | Exportation des règles de pare-feu | Portail Azure | Trimestrielle |
| Sécurité réseau | Exportation des règles NSG | Portail Azure | Trimestrielle |
| Journalisation | Paramètres de diagnostic | Portail Azure | Trimestrielle |
| Journalisation | Rétention Log Analytics | Portail Azure | Trimestrielle |
| Vulnérabilité | Recommandations Defender | Portail Azure | Hebdomadaire |
| Vulnérabilité | Rapport de vulnérabilités | Defender | Mensuelle |
| Conformité | Conformité Azure Policy | Portail Azure | Hebdomadaire |
| Conformité | Score de sécurité Defender | Portail Azure | Hebdomadaire |
| Gestion des changements | Enregistrements de changement | Outil GSTI | Continue |
| Intervention en cas d'incident | Enregistrements d'incident | GSTI/Sentinel | Continue |

---

# ANNEXE C : MODÈLE D'HÉRITAGE DES CONTRÔLES

## C.1 Aperçu de l'héritage

Les charges de travail clients héritent des contrôles de la couche plateforme. Cette annexe documente quels contrôles sont hérités, partiellement hérités ou mis en œuvre par le client.

## C.2 Contrôles entièrement hérités

Les clients héritent entièrement de ces contrôles sans mise en œuvre supplémentaire :

- Sécurité physique (Microsoft)
- Configuration de la sécurité du locataire
- Sécurité du périmètre réseau (Pare-feu Azure)
- Infrastructure de journalisation centralisée
- Infrastructure SIEM et de détection des menaces
- Fournisseur d'identité de la plateforme
- Politiques d'accès conditionnel
- Procédures d'urgence
- Sécurité DNS
- Protection DDoS

## C.3 Contrôles partiellement hérités

Les clients héritent des contrôles de base mais doivent mettre en œuvre des exigences propres aux charges de travail :

| La plateforme fournit | Le client met en œuvre |
|----------------------|------------------------|
| Sécurité du réseau hub | Règles NSG des spokes |
| Journalisation centralisée | Paramètres de diagnostic des charges de travail |
| Defender pour le cloud | Recommandations de sécurité des charges de travail |
| Infrastructure d'analyse des vulnérabilités | Correction des charges de travail |
| Infrastructure Key Vault | Secrets des charges de travail |
| Infrastructure de sauvegarde | Politiques de sauvegarde des charges de travail |

## C.4 Contrôles mis en œuvre par le client

Les clients doivent mettre en œuvre entièrement ces contrôles :

- Authentification/autorisation des applications
- Sécurité du code d'application
- Classification des données
- Décisions de chiffrement des données
- Journalisation des applications
- Contrôle d'accès propre aux charges de travail
- Gestion des vulnérabilités des applications
- Procédures RS des charges de travail

---

# ANNEXE D : GLOSSAIRE

| Terme | Définition |
|-------|------------|
| Pare-feu Azure | Service de sécurité réseau natif du nuage |
| Azure Policy | Service de gouvernance et de conformité Azure |
| CCC | Comité consultatif des changements |
| CCCS | Centre canadien pour la cybersécurité |
| Accès conditionnel | Contrôle d'accès basé sur les politiques Azure AD |
| RS | Reprise après sinistre |
| Entra ID | Service d'identité infonuagique de Microsoft (anciennement Azure AD) |
| Hub | Réseau central fournissant des services partagés |
| IaC | Infrastructure en tant que code |
| ITSG-33 | Gestion des risques liés à la sécurité des TI : Une approche axée sur le cycle de vie |
| JAT | Accès juste-à-temps |
| IM/DM | Intégrité moyenne / Disponibilité moyenne |
| AMF | Authentification multifacteur |
| NSG | Groupe de sécurité réseau |
| PaaS | Plateforme en tant que service |
| PBMM | Protégé B / Moyen / Moyen |
| PIM | Gestion des identités privilégiées |
| RBAC | Contrôle d'accès basé sur les rôles |
| OPR | Objectif de point de reprise |
| OTR | Objectif de temps de reprise |
| EAS | Évaluation et autorisation de sécurité |
| Sentinel | SIEM natif du nuage de Microsoft |
| SIEM | Gestion des informations et des événements de sécurité |
| COS | Centre des opérations de sécurité |
| Spoke | Réseau virtuel de charge de travail client |
| SSE | Chiffrement du service de stockage |
| TDE | Chiffrement transparent des données |
| TLS | Sécurité de la couche de transport |

---

**FIN DU DOCUMENT**

---

*Ce document est PROTÉGÉ B lorsqu'il contient des informations propres au système.*

*Classification du document vierge : NON CLASSIFIÉ*
