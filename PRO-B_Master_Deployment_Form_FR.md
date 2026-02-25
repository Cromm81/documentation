# ENVIRONNEMENT PROTÉGÉ B
# FORMULAIRE MAÎTRE DE DEMANDE DE DÉPLOIEMENT

**Gouvernement du Canada — Autorisation de déploiement technologique**

> **INSTRUCTIONS :** Ce formulaire modulaire couvre tous les types de déploiement technologique. Sélectionnez uniquement les sections pertinentes à votre déploiement spécifique. Les sections marquées ⚙️ sont OBLIGATOIRES pour toutes les soumissions. Les sections marquées 📋 sont CONDITIONNELLES selon le type de déploiement.

---

## ⚙️ SECTION 1 : APERÇU DU PROJET ET TYPE DE DÉPLOIEMENT

| Champ | Description | Requis |
|-------|-------------|--------|
| **Nom du projet** | | Oui |
| **ID du projet** | | Oui |
| **Date de déploiement** | | Oui |
| **Type de technologie** | ☐ RPN ☐ Pare-feu ☐ Équilibreur de charge ☐ Passerelle API ☐ Commutateur réseau ☐ Routeur ☐ IDS/IPS ☐ WAF ☐ Autre : _____ | Oui |
| **Nom du demandeur** | | Oui |
| **Titre du demandeur** | | Oui |
| **Courriel du demandeur** | | Oui |
| **Téléphone du demandeur** | | Oui |
| **Autorité approbatrice** | | Oui |
| **Code budgétaire** | | Non |

---

## ⚙️ SECTION 2 : RÉSUMÉ EXÉCUTIF

**Justification commerciale :**
> _____________________________________________________________________________
> _____________________________________________________________________________

**Avantages attendus :**
> _____________________________________________________________________________
> _____________________________________________________________________________

**Calendrier du projet :**

| Jalon | Date cible |
|-------|------------|
| Planification terminée | |
| Tests terminés | |
| Déploiement en production | |
| Revue post-implantation | |

---

## ⚙️ SECTION 3 : INVENTAIRE DE L'INFRASTRUCTURE ET DES SYSTÈMES

| Nom du système/composant | Type | Nom d'hôte | Adresse IP | Environnement | Propriétaire | Remarques |
|--------------------------|------|------------|------------|---------------|--------------|-----------|
| | | | | ☐ Dév ☐ Test ☐ Prod | | |
| | | | | ☐ Dév ☐ Test ☐ Prod | | |
| | | | | ☐ Dév ☐ Test ☐ Prod | | |
| | | | | ☐ Dév ☐ Test ☐ Prod | | |
| | | | | ☐ Dév ☐ Test ☐ Prod | | |

---

## ⚙️ SECTION 4 : MATRICE DE COMMUNICATION RÉSEAU (INTERNE)

| Source | Destination | Protocole | Port(s) | Direction | Objet | Chiffré |
|--------|-------------|-----------|---------|-----------|-------|---------|
| | | ☐ TCP ☐ UDP ☐ ICMP | | ☐ Entrant ☐ Sortant ☐ Les deux | | ☐ Oui ☐ Non |
| | | ☐ TCP ☐ UDP ☐ ICMP | | ☐ Entrant ☐ Sortant ☐ Les deux | | ☐ Oui ☐ Non |
| | | ☐ TCP ☐ UDP ☐ ICMP | | ☐ Entrant ☐ Sortant ☐ Les deux | | ☐ Oui ☐ Non |
| | | ☐ TCP ☐ UDP ☐ ICMP | | ☐ Entrant ☐ Sortant ☐ Les deux | | ☐ Oui ☐ Non |
| | | ☐ TCP ☐ UDP ☐ ICMP | | ☐ Entrant ☐ Sortant ☐ Les deux | | ☐ Oui ☐ Non |

---

## 📋 SECTION 5 : COMMUNICATION EXTERNE

*Requis pour les déploiements avec connectivité réseau externe*

| Source | Destination | Protocole | Port(s) | Fréquence | Sensibilité | Chiffré |
|--------|-------------|-----------|---------|-----------|-------------|---------|
| | | | | ☐ Continu ☐ Planifié | ☐ Public ☐ Interne ☐ Confidentiel | ☐ Oui ☐ Non |
| | | | | ☐ Continu ☐ Planifié | ☐ Public ☐ Interne ☐ Confidentiel | ☐ Oui ☐ Non |
| | | | | ☐ Continu ☐ Planifié | ☐ Public ☐ Interne ☐ Confidentiel | ☐ Oui ☐ Non |

---

## ⚙️ SECTION 6 : EXIGENCES EN MATIÈRE DE SÉCURITÉ ET DE CHIFFREMENT

### Classification des données
☐ Non classifié  ☐ Protégé A  ☐ Protégé B  ☐ Secret  ☐ Très secret

### Chiffrement en transit (selon ITSP.40.111)
☐ TLS 1.2  ☐ TLS 1.3  ☐ IPSec  ☐ SSH  ☐ Autre : _____________________

### Chiffrement au repos
☐ AES-256  ☐ AES-192  ☐ AES-128  ☐ S/O

### Méthodes d'authentification
☐ Nom d'utilisateur/Mot de passe  
☐ Authentification multifacteur (AMF)  
☐ Basée sur les certificats  
☐ OAuth 2.0  
☐ SAML 2.0  
☐ Kerberos  
☐ Autre : _____________________

### Modèle de contrôle d'accès
☐ Contrôle d'accès basé sur les rôles (CABR)  
☐ Contrôle d'accès basé sur les attributs (CABA)  
☐ Architecture à confiance zéro  

### Principe du moindre privilège
☐ Implémenté  ☐ Planifié  ☐ Non applicable

---

## 📋 SECTION 7 : RÈGLES DE SÉCURITÉ PARE-FEU ET RÉSEAU

*Requis pour les déploiements de pare-feu, RPN et périmètre*

| Règle # | Source | Destination | Protocole | Port(s) | Action | Journalisation | Priorité |
|---------|--------|-------------|-----------|---------|--------|----------------|----------|
| | | | | | ☐ Autoriser ☐ Refuser | ☐ Oui ☐ Non | ☐ Élevée ☐ Moy ☐ Basse |
| | | | | | ☐ Autoriser ☐ Refuser | ☐ Oui ☐ Non | ☐ Élevée ☐ Moy ☐ Basse |
| | | | | | ☐ Autoriser ☐ Refuser | ☐ Oui ☐ Non | ☐ Élevée ☐ Moy ☐ Basse |
| | | | | | ☐ Autoriser ☐ Refuser | ☐ Oui ☐ Non | ☐ Élevée ☐ Moy ☐ Basse |
| | | | | | ☐ Autoriser ☐ Refuser | ☐ Oui ☐ Non | ☐ Élevée ☐ Moy ☐ Basse |

**Politique par défaut :** ☐ Tout refuser (Liste blanche)  ☐ Tout autoriser (Liste noire)

---

## ⚙️ SECTION 8 : EXIGENCES DE CONFORMITÉ ET DE RÉGLEMENTATION

### Cadres applicables (sélectionner tous ceux qui s'appliquent)
☐ ITSP.40.111 (Algorithmes cryptographiques pour non classifié, Protégé A et B)  
☐ LPRPDE (Loi sur la protection des renseignements personnels et les documents électroniques)  
☐ SOC 2 Type II  
☐ ISO 27001  
☐ Cadre de cybersécurité du NIST (Adoption du GC)  
☐ Politique sur les communications et l'image de marque  
☐ Politique sur les services et le numérique du SCT  
☐ Directive sur la gestion de la sécurité du SCT  
☐ Autre : _____________________

### Exigences de résidence des données
☐ Canada seulement  ☐ Amérique du Nord  ☐ International (préciser) : _____________________

### Exigences de journalisation
**Niveau :** ☐ Minimal  ☐ Standard  ☐ Complet  ☐ Médico-légal

**Période de rétention :** ☐ 30 jours  ☐ 90 jours  ☐ 1 an  ☐ 7 ans  ☐ Autre : _____

### Réponse aux incidents
**Plan de réponse aux incidents en place :** ☐ Oui  ☐ Non

**Délai de signalement des événements :** ☐ Immédiat  ☐ 24 heures  ☐ 72 heures  ☐ Selon l'ALS

---

## 📋 SECTION 9 : GESTION DES VULNÉRABILITÉS ET CORRECTIFS

*Requis pour tous les déploiements exposés à Internet ou d'infrastructure critique*

### Fréquence d'analyse des vulnérabilités
☐ Hebdomadaire  ☐ Mensuelle  ☐ Trimestrielle  ☐ S/O

### Calendrier des correctifs
| Gravité | Délai |
|---------|-------|
| Critique/Urgence | ☐ 24 heures  ☐ 48 heures  ☐ 72 heures |
| Élevée/Urgent | ☐ 1 semaine  ☐ 2 semaines |
| Moyenne/Régulier | ☐ 30 jours  ☐ 60 jours |
| Basse | ☐ Prochaine fenêtre de maintenance |

---

## 📋 SECTION 10 : PROTECTION CONTRE LES CYBERMENACES ET LES ATTAQUES DDoS

*Requis pour les déploiements exposés à Internet*

### Atténuation des attaques DDoS
**Activée :** ☐ Oui  ☐ Non

**Type :** ☐ Filtrage basé sur le débit  ☐ Analyse comportementale  ☐ Intégration WAF  ☐ Basé sur CDN

### Système de détection/prévention des intrusions (IDS/IPS)
**Activé :** ☐ Oui  ☐ Non

**Mode :** ☐ Détection seulement  ☐ Prévention  ☐ Les deux

### Intégration des flux de menaces du GC
**Activée :** ☐ Oui  ☐ Non

**Mises à jour en temps réel :** ☐ Oui  ☐ Non

---

## 📋 SECTION 11 : ANALYSE DES PAQUETS ET SURVEILLANCE DU RÉSEAU

*Requis pour les déploiements d'infrastructure réseau*

### Technologies de surveillance
☐ NetFlow  
☐ sFlow  
☐ IPFIX  
☐ Capture complète des paquets  
☐ Inspection approfondie des paquets (DPI)  
☐ SNMP  
☐ Autre : _____________________

### Surveillance de la bande passante
☐ Requise  ☐ Non requise

**Bande passante attendue :** __________ Mbps/Gbps

### Qualité de service (QoS)
☐ Requise  ☐ Non requise

**Exigences d'ALS :** _____________________

---

## ⚙️ SECTION 12 : SAUVEGARDE ET REPRISE APRÈS SINISTRE

### Stratégie de sauvegarde
☐ Sauvegarde complète  
☐ Incrémentale  
☐ Différentielle  
☐ Réplication continue  
☐ S/O

### Objectifs de récupération
| Métrique | Valeur |
|----------|--------|
| **OTR (Objectif de temps de rétablissement)** | __________ heures/jours |
| **OPR (Objectif de point de rétablissement)** | __________ heures |

### Emplacement de la sauvegarde
☐ Sur site  ☐ Infonuagique (approuvé par le GC)  ☐ Géo-redondant  ☐ Hybride

### Fréquence des tests de sauvegarde
☐ Mensuelle  ☐ Trimestrielle  ☐ Annuelle  ☐ S/O

---

## ⚙️ SECTION 13 : GESTION DES CHANGEMENTS ET TESTS

### Tests de préproduction
☐ Requis  ☐ Non requis

### Environnement(s) de test
☐ Développement  ☐ Test  ☐ Mise en scène  ☐ Production (limité)

### Approbation du comité consultatif des changements (CCC)
☐ Requise  ☐ Non requise

### Plan de retour en arrière documenté
☐ Oui  ☐ Non

---

## 📋 SECTION 14 : INFORMATION SUR LES FOURNISSEURS ET TIERS

| Fournisseur/Produit | Version | Niveau d'assistance | ALS | Certification de sécurité | Remarques |
|---------------------|---------|---------------------|-----|---------------------------|-----------|
| | | ☐ Platine ☐ Or ☐ Argent ☐ Bronze | | ☐ SOC 2 ☐ ISO 27001 ☐ FedRAMP | |
| | | ☐ Platine ☐ Or ☐ Argent ☐ Bronze | | ☐ SOC 2 ☐ ISO 27001 ☐ FedRAMP | |
| | | ☐ Platine ☐ Or ☐ Argent ☐ Bronze | | ☐ SOC 2 ☐ ISO 27001 ☐ FedRAMP | |

---

## SECTION 15 : EXIGENCES SUPPLÉMENTAIRES ET COMMENTAIRES

> _____________________________________________________________________________
> _____________________________________________________________________________
> _____________________________________________________________________________
> _____________________________________________________________________________

---

## ⚙️ SECTION 16 : APPROBATIONS ET SIGNATURES

| Rôle | Nom | Titre | Signature | Date |
|------|-----|-------|-----------|------|
| **Demandeur** | | | | |
| **Chef technique** | | | | |
| **Agent de sécurité** | | | | |
| **Agent de conformité** | | | | |
| **Autorité approbatrice** | | | | |

---

**Version du document :** 1.0  
**Classification :** Protégé B  
**Dernière mise à jour :** _____________________

---

*Ce formulaire est conçu pour répondre aux exigences du gouvernement du Canada pour les déploiements technologiques de niveau Protégé B. Assurez-vous que toutes les sections applicables sont complétées avant la soumission.*
