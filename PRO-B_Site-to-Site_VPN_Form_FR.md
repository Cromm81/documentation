# ENVIRONNEMENT PROTÉGÉ B
# FORMULAIRE DE DEMANDE DE DÉPLOIEMENT RPN DE SITE À SITE

**Gouvernement du Canada — Autorisation de tunnel RPN**

---

## SECTION 1 : APERÇU DU PROJET

| Champ | Valeur |
|-------|--------|
| **Nom du projet RPN** | |
| **ID du projet** | |
| **Date de déploiement** | |
| **Nom du demandeur** | |
| **Titre du demandeur** | |
| **Courriel du demandeur** | |
| **Téléphone du demandeur** | |
| **Autorité approbatrice** | |

---

## SECTION 2 : POINTS TERMINAUX DU RPN

### Site A (Local)

| Champ | Valeur |
|-------|--------|
| **Nom du site** | |
| **Emplacement physique** | |
| **Adresse IP publique** | |
| **Plage IP interne/Sous-réseau** | |
| **Nom du contact principal** | |
| **Courriel du contact principal** | |
| **Téléphone du contact principal** | |

### Site B (Distant)

| Champ | Valeur |
|-------|--------|
| **Nom du site** | |
| **Emplacement physique** | |
| **Adresse IP publique** | |
| **Plage IP interne/Sous-réseau** | |
| **Nom du contact principal** | |
| **Courriel du contact principal** | |
| **Téléphone du contact principal** | |

---

## SECTION 3 : SPÉCIFICATIONS DU TUNNEL RPN

### Sélection du protocole
☐ IPSec (IKEv2) — *Recommandé*  
☐ IPSec (IKEv1)  
☐ WireGuard  
☐ OpenVPN  
☐ Autre : _____________________

### Paramètres de Phase 1 (IKE)
| Paramètre | Valeur |
|-----------|--------|
| **Algorithme de chiffrement** | ☐ AES-256 ☐ AES-192 ☐ AES-128 |
| **Algorithme de hachage** | ☐ SHA-256 ☐ SHA-384 ☐ SHA-512 |
| **Groupe DH** | ☐ Groupe 14 ☐ Groupe 19 ☐ Groupe 20 ☐ Groupe 21 |
| **Durée de vie de l'AS** | __________ secondes |

### Paramètres de Phase 2 (IPSec)
| Paramètre | Valeur |
|-----------|--------|
| **Algorithme de chiffrement** | ☐ AES-256 ☐ AES-192 ☐ AES-128 |
| **Algorithme de hachage** | ☐ SHA-256 ☐ SHA-384 ☐ SHA-512 |
| **Groupe PFS** | ☐ Groupe 14 ☐ Groupe 19 ☐ Groupe 20 ☐ Aucun |
| **Durée de vie de l'AS** | __________ secondes |

### Méthode d'authentification
☐ Clé prépartagée (CPP)  
☐ Certificats X.509  
☐ EAP  
☐ Autre : _____________________

**Si CPP :** La clé sera échangée via : ☐ Canal sécurisé  ☐ En personne  ☐ Courriel chiffré

---

## SECTION 4 : TRAFIC RÉSEAU ET ROUTAGE

### Flux de trafic autorisés

| Réseau source | Réseau destination | Protocole | Port(s) | Objet |
|---------------|-------------------|-----------|---------|-------|
| | | ☐ TCP ☐ UDP ☐ Les deux | | |
| | | ☐ TCP ☐ UDP ☐ Les deux | | |
| | | ☐ TCP ☐ UDP ☐ Les deux | | |
| | | ☐ TCP ☐ UDP ☐ Les deux | | |
| | | ☐ TCP ☐ UDP ☐ Les deux | | |

### Configuration du routage
**Type de routage :** ☐ Statique  ☐ Dynamique (BGP)  ☐ Basé sur les politiques

**NAT requis :** ☐ Oui  ☐ Non

Si oui, préciser la configuration NAT :
> _____________________________________________________________________________

---

## SECTION 5 : RÈGLES DE PARE-FEU

### Règles requises
☐ Entrantes  ☐ Sortantes  ☐ Les deux

### Règles de pare-feu du Site A

| Règle # | Source | Destination | Protocole | Port(s) | Action |
|---------|--------|-------------|-----------|---------|--------|
| | | | | | ☐ Autoriser ☐ Refuser |
| | | | | | ☐ Autoriser ☐ Refuser |
| | | | | | ☐ Autoriser ☐ Refuser |

### Règles de pare-feu du Site B

| Règle # | Source | Destination | Protocole | Port(s) | Action |
|---------|--------|-------------|-----------|---------|--------|
| | | | | | ☐ Autoriser ☐ Refuser |
| | | | | | ☐ Autoriser ☐ Refuser |
| | | | | | ☐ Autoriser ☐ Refuser |

### Ports IKE/IPSec requis
☐ UDP 500 (IKE)  
☐ UDP 4500 (NAT-T)  
☐ Protocole ESP 50  
☐ Protocole AH 51  

---

## SECTION 6 : SÉCURITÉ ET CONFORMITÉ

### Classification des données
☐ Non classifié  ☐ Protégé A  ☐ Protégé B

### Exigences de conformité
☐ ITSP.40.111 (Normes cryptographiques)  
☐ LPRPDE  
☐ SOC 2  
☐ ISO 27001  
☐ Autre : _____________________

### Résidence des données
☐ Canada seulement  ☐ Amérique du Nord  ☐ International

### Délai de signalement des incidents
☐ Immédiat  ☐ 24 heures  ☐ 72 heures  ☐ Selon l'ALS

---

## SECTION 7 : SURVEILLANCE ET JOURNALISATION

### Niveau de journalisation
☐ Minimal (connexion établie/fermée seulement)  
☐ Standard (événements de connexion + erreurs)  
☐ Complet (toutes les métadonnées de trafic)  

### Période de rétention des journaux
☐ 30 jours  ☐ 90 jours  ☐ 1 an  ☐ 7 ans

### Exigences de surveillance
**Surveillance de la bande passante :** ☐ Requise  ☐ Non requise

**Bande passante attendue :** __________ Mbps

**Alertes requises :** ☐ Oui  ☐ Non

Si oui, alerter sur :
☐ Tunnel hors service  
☐ Latence élevée (seuil : _____ ms)  
☐ Perte de paquets (seuil : _____ %)  
☐ Seuil de bande passante (seuil : _____ Mbps)  

---

## SECTION 8 : HAUTE DISPONIBILITÉ ET BASCULEMENT

### Basculement requis
☐ Oui  ☐ Non

### Configuration du basculement (si applicable)

| Champ | Valeur |
|-------|--------|
| **Point terminal RPN de secours (Site A)** | |
| **Point terminal RPN de secours (Site B)** | |
| **Type de basculement** | ☐ Actif/Passif ☐ Actif/Actif |
| **Déclencheur de basculement** | ☐ Automatique ☐ Manuel |

### Objectifs de récupération
| Métrique | Valeur |
|----------|--------|
| **OTR (Objectif de temps de rétablissement)** | __________ minutes |
| **OPR (Objectif de point de rétablissement)** | __________ minutes |

---

## SECTION 9 : INFORMATION SUR LES FOURNISSEURS

### Solution RPN

| Champ | Valeur |
|-------|--------|
| **Fournisseur** | |
| **Nom du produit** | |
| **Version/Micrologiciel** | |
| **Niveau d'assistance** | ☐ Platine ☐ Or ☐ Argent ☐ Bronze |
| **ALS d'assistance** | |
| **Certifications de sécurité** | ☐ SOC 2 ☐ ISO 27001 ☐ Critères communs ☐ FIPS 140-2/3 |

---

## SECTION 10 : TESTS ET VALIDATION

### Tests de prédéploiement
☐ Requis  ☐ Non requis

### Plan de test
| Test | Description | Réussite/Échec |
|------|-------------|----------------|
| Établissement du tunnel | Vérifier que le tunnel s'établit correctement | |
| Flux de trafic | Vérifier que le trafic autorisé passe | |
| Basculement | Tester le basculement vers la sauvegarde (si applicable) | |
| Performance | Vérifier que la bande passante répond aux exigences | |
| Sécurité | Vérifier que le trafic non autorisé est bloqué | |

### Environnement de test
☐ Laboratoire  ☐ Dév  ☐ Mise en scène  ☐ Production (limité)

---

## SECTION 11 : REMARQUES ET EXIGENCES SUPPLÉMENTAIRES

> _____________________________________________________________________________
> _____________________________________________________________________________
> _____________________________________________________________________________
> _____________________________________________________________________________

---

## SECTION 12 : APPROBATIONS

| Rôle | Nom | Titre | Signature | Date |
|------|-----|-------|-----------|------|
| **Demandeur** | | | | |
| **Chef technique** | | | | |
| **Administrateur réseau** | | | | |
| **Agent de sécurité** | | | | |
| **Autorité approbatrice** | | | | |

---

**Version du document :** 1.0  
**Classification :** Protégé B  
**Dernière mise à jour :** _____________________

---

*Ce formulaire est conçu spécifiquement pour les déploiements de RPN de site à site dans les environnements Protégé B du gouvernement du Canada.*
