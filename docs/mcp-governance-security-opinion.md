# Opinion de sécurité GRC — Gouvernance des serveurs MCP

> **Statut :** Proposition pour revue — non approuvée  
> **Portée :** Organisationnelle (serveurs MCP internes, tiers, locaux et distants)  
> **Perspective :** Gouvernance des risques et conformité, deuxième ligne de défense (2LoD)  
> **Confidentialité :** Exemple générique et anonymisé ; ne constitue pas une description vérifiée des contrôles d'une organisation particulière.

## 1. Considérations de sécurité

### 1.1 Contexte et enjeux de gouvernance
Le Model Context Protocol (MCP) permet aux applications et agents IA d'interagir avec des outils, ressources et systèmes externes. Son adoption multiplie les chemins d'accès aux données et les capacités d'action. La gouvernance doit couvrir non seulement le serveur, mais aussi le client, les outils, les identités, les systèmes cibles et les flux associés. Une intégration en production ne constitue pas en soi une preuve d'autorisation ou de conformité.

### 1.2 Responsabilités et visibilité
L'absence d'inventaire, de propriétaire désigné ou de processus d'autorisation vérifiable peut empêcher l'organisation de connaître son exposition. Les responsabilités métier, techniques, d'architecture et de sécurité doivent être distinctes. La 1LoD possède et exploite les contrôles ; la 2LoD formule les attentes et exerce une surveillance indépendante. Les lacunes supposées doivent être confirmées avant d'être qualifiées de constats.

### 1.3 Identités et privilèges
Les serveurs MCP peuvent utiliser des identités utilisateur ou techniques, avec des autorisations différentes de celles de l'utilisateur initiateur. Les risques incluent la confusion d'identité, les privilèges excessifs et l'accès indirect à des ressources protégées. Les autorisations doivent être appréciées sur l'ensemble de la chaîne client–serveur–système cible.

### 1.4 Données et frontières de confiance
Même un outil limité à la lecture peut exposer des informations sensibles à grande échelle. Les transferts vers des fournisseurs ou modèles externes doivent être examinés selon la classification des données, la finalité du traitement et les obligations applicables. Les frontières de confiance et les destinations de données doivent être documentées.

### 1.5 Menaces MCP et agents IA
Les scénarios à considérer comprennent la prompt injection, le *tool poisoning*, la manipulation des réponses d'outils, l'exfiltration, les dépendances compromises et le détournement des capacités des agents. Les descriptions et résultats d'outils ne doivent pas être traités comme des instructions de confiance. L'approbation d'un fournisseur ne vaut pas approbation de chaque outil ou intégration.

### 1.6 Fournisseurs et chaîne d'approvisionnement
Les serveurs tiers peuvent évoluer sans contrôle direct de l'organisation. Les garanties fournisseur, l'intégrité des composants, les dépendances, les vulnérabilités et les changements fonctionnels influencent le risque résiduel.

### 1.7 Traçabilité et confidentialité des journaux
La traçabilité des identités, appels d'outils, décisions d'autorisation et opérations est nécessaire pour l'investigation et l'imputabilité. La journalisation intégrale des requêtes et réponses peut cependant reproduire des secrets et données confidentielles ; elle nécessite une justification explicite, des protections et une durée de conservation adaptée.

### 1.8 Cycle de vie et assurance
Les risques évoluent avec les capacités, privilèges, clients, versions et systèmes connectés. L'évaluation initiale doit être complétée par des réexamens fondés sur la criticité et les changements significatifs. Les déploiements existants doivent également être évalués.

## 2. Recommandations de sécurité

### 2.1 Instituer une gouvernance formalisée
Définir un cadre couvrant toute intégration MCP, avec propriétaires désignés, responsabilités, étapes d'autorisation, critères de refus et processus de retrait. Prévoir une décision conjointe métier–architecture–sécurité selon les délégations en vigueur, sans attribuer automatiquement à la 2LoD l'acceptation des risques métier.

### 2.2 Tenir un inventaire centralisé
Recenser au minimum : propriétaire, fournisseur, client IA, serveur et hébergement, outils/capacités, systèmes et classes de données accessibles, identités, flux externes, niveau de risque, date de revue et statut d'autorisation. Prévoir des mécanismes d'identification des intégrations non déclarées.

### 2.3 Évaluer les risques par intégration
Réaliser avant production une évaluation documentée tenant compte de la sensibilité des données, des privilèges, des capacités de lecture/écriture/exécution, de l'exposition, des dépendances et de la criticité métier. Proposer des niveaux de risque compatibles avec la méthode organisationnelle, sans imposer de grille parallèle. Renforcer l'assurance et la revue indépendante pour les cas sensibles.

### 2.4 Appliquer le moindre privilège
Privilégier des identités individualisées lorsque pertinent ; encadrer les comptes techniques, la délégation d'accès, les jetons, les secrets, les durées de validité et la révocation. Vérifier qu'un serveur n'élargit pas implicitement les droits du demandeur. Réviser les permissions périodiquement.

### 2.5 Protéger les données et les flux
Documenter les sources, destinations et finalités. Appliquer les règles de classification, les restrictions de transfert et les exigences de confidentialité. Limiter l'accès et les volumes de données aux besoins autorisés, y compris pour les outils en lecture seule.

### 2.6 Vérifier la sécurité des serveurs et outils
Exiger des mesures proportionnées de validation des composants, gestion des vulnérabilités, isolation, contrôle des capacités, limitation des privilèges et détection d'abus. Tester les scénarios de prompt injection et de tool poisoning. Réévaluer les changements significatifs des descriptions d'outils, dépendances ou permissions.

### 2.7 Encadrer les fournisseurs tiers
Autoriser uniquement les fournisseurs préapprouvés, puis évaluer séparément chaque intégration et ses capacités. Examiner les garanties contractuelles, la sécurité des données, la sous-traitance, les mises à jour et les conditions de retrait.

### 2.8 Assurer la journalisation et la surveillance
Conserver des traces exploitables des identités, appels d'outils, décisions d'autorisation, opérations et corrélations de bout en bout. Étudier la journalisation exhaustive des requêtes/réponses selon les besoins d'investigation, avec filtrage ou masquage des secrets, contrôle d'accès, chiffrement, durée de rétention, surveillance et suppression appropriés. Ne pas imposer une conservation brute universelle sans analyse de confidentialité.

### 2.9 Gérer changements, écarts et exceptions
Intégrer les serveurs MCP aux processus de changements, vulnérabilités et incidents. Traiter les non-conformités selon le risque : restriction, remédiation datée, exception formelle ou retrait. L'acceptation du risque résiduel appartient au propriétaire habilité, avec justification, échéance et contrôles compensatoires si nécessaires.

### 2.10 Régulariser les déploiements existants
Mettre en place une transition comprenant inventaire, désignation des propriétaires, réévaluation de **tous** les serveurs en production, priorisation des remédiations et échéances. Prévoir des revues périodiques selon la criticité et à chaque changement significatif. La 2LoD suit les écarts, exceptions et preuves d'assurance.

### Position de sécurité proposée
L'adoption et le maintien des intégrations MCP peuvent être autorisés **sous conditions** : responsabilités établies, visibilité sur les capacités et les flux, évaluation proportionnée des risques, contrôles minimaux vérifiables et décision documentée par les autorités compétentes. L'autorisation vise **l'intégration et son contexte d'utilisation**, non le seul serveur ou fournisseur.

### Points restant à arbitrer avant approbation
- Critères et niveaux de classification des risques compatibles avec le référentiel interne.
- Modalités d'autorisation des opérations sensibles.
- Granularité, minimisation et durée de conservation des journaux MCP.
- Preuves minimales d'assurance et seuils de revue indépendante.
- Délais de régularisation, conditions d'exception et autorités d'approbation.

---
*Document de travail générique et anonymisé, destiné à une revue GRC et technique avant adoption formelle.*
