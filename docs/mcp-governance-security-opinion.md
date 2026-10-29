# Opinion de sécurité — Gouvernance des serveurs MCP (Model Context Protocol)

**Nature :** Opinion de sécurité GRC — Deuxième ligne de défense (2LoD)  
**Portée :** Organisationnelle  
**Statut :** Projet d'opinion soumis à validation

## 1. Considérations de sécurité

### 1.1. Contexte et enjeux de gouvernance

Le Model Context Protocol (MCP) permet aux applications et agents d'intelligence artificielle d'interagir avec des systèmes, des sources de données et des outils externes au moyen d'interfaces standardisées.

Cette capacité facilite l'intégration de l'intelligence artificielle aux processus organisationnels, mais introduit également de nouvelles surfaces d'attaque et des enjeux de gouvernance liés à l'accès aux données, à la délégation des privilèges et à l'exécution d'actions par des systèmes d'intelligence artificielle.

L'utilisation de serveurs MCP, qu'ils soient développés en interne, fournis par des tiers, exécutés localement ou hébergés à distance, nécessite par conséquent un encadrement de sécurité cohérent à l'échelle de l'organisation.

La présence de serveurs MCP déjà utilisés en production renforce l'importance de disposer d'une visibilité centralisée sur ces intégrations et de mécanismes permettant d'en évaluer et d'en surveiller les risques.

### 1.2. Gouvernance et responsabilités

L'absence d'un cadre de gouvernance clairement identifié peut favoriser l'introduction de serveurs MCP sans évaluation préalable des risques, sans attribution formelle des responsabilités et sans suivi adéquat de leur cycle de vie.

La gouvernance doit considérer non seulement le serveur MCP, mais également son contexte d'intégration, notamment les applications clientes, les outils exposés, les identités utilisées, les systèmes accessibles et les flux de données associés.

Les responsabilités doivent être clairement établies entre les propriétaires métier, les équipes techniques, les fonctions d'architecture et les fonctions de sécurité.

La première ligne de défense demeure responsable de l'identification et de la maîtrise opérationnelle des risques, tandis que la deuxième ligne définit les attentes de sécurité et exerce une surveillance indépendante.

### 1.3. Gestion des identités et des privilèges

Les serveurs MCP peuvent accéder aux systèmes organisationnels au moyen d'identités individuelles ou techniques. Selon leur configuration, ils peuvent également disposer de privilèges différents de ceux des utilisateurs à l'origine des demandes.

Cette situation introduit notamment des risques d'accès excessifs, de confusion des identités, d'utilisation inappropriée de comptes techniques et d'élévation indirecte des privilèges.

L'application du principe du moindre privilège, la séparation des responsabilités et la traçabilité des accès constituent des éléments fondamentaux de la maîtrise de ces risques.

Une attention particulière doit être portée à la délégation des autorisations entre les utilisateurs, les applications clientes, les serveurs MCP et les systèmes sous-jacents.

### 1.4. Protection des données et frontières de confiance

Les serveurs MCP peuvent donner accès à des informations organisationnelles de différentes sensibilités, notamment des documents internes, des dépôts de code, des données métier et des informations confidentielles.

Même lorsqu'un serveur MCP dispose uniquement de capacités de consultation, l'étendue de ses accès peut présenter des risques significatifs de divulgation ou d'exfiltration.

Ces risques sont amplifiés lorsque des données sont transmises à des applications, des modèles ou des services externes à l'organisation.

Les frontières de confiance entre les différentes composantes doivent donc être identifiées et les flux de données évalués au regard des politiques de classification, de confidentialité et de protection de l'information applicables.

### 1.5. Menaces propres aux intégrations MCP et aux agents IA

Les intégrations MCP sont exposées à des menaces qui combinent les risques traditionnels de sécurité applicative et ceux associés aux systèmes d'intelligence artificielle.

Parmi ces menaces figurent notamment les attaques par injection de prompt, la manipulation des descriptions ou des réponses des outils (*tool poisoning*), l'exploitation de dépendances compromises, le détournement des capacités des agents et l'utilisation non autorisée de ressources.

L'approbation d'un serveur MCP ou de son fournisseur ne garantit pas à elle seule la fiabilité des informations et instructions transmises à travers ses outils.

Les contenus provenant de sources externes ou insuffisamment fiables doivent être considérés comme des données non fiables, et non comme des instructions autorisées à modifier les règles de sécurité.

### 1.6. Risques liés aux fournisseurs et composants tiers

Le recours à des serveurs MCP externes introduit des dépendances à des fournisseurs, des composants logiciels et des services pouvant évoluer indépendamment des mécanismes de contrôle de l'organisation.

Ces dépendances soulèvent des enjeux liés à la provenance des composants, à la gestion des vulnérabilités, à la protection des données, aux modifications des fonctionnalités et aux conditions d'utilisation.

L'approbation d'un fournisseur ne doit pas être assimilée à une autorisation générale de l'ensemble de ses serveurs, outils ou intégrations.

Chaque utilisation doit être appréciée selon son contexte et les risques qu'elle introduit.

### 1.7. Journalisation, surveillance et capacité d'investigation

La capacité à retracer les interactions entre les clients IA, les serveurs MCP et les systèmes organisationnels constitue une condition importante de l'imputabilité, de la détection des comportements anormaux et de l'investigation des incidents.

La journalisation doit permettre de reconstituer les interactions pertinentes, notamment les identités impliquées, les outils invoqués, les décisions d'autorisation et les opérations réalisées.

Toutefois, la conservation des requêtes et réponses complètes peut elle-même introduire des risques de confidentialité et d'exposition de renseignements sensibles.

La portée, la granularité, la protection et la durée de conservation des journaux doivent être déterminées en fonction des risques et des obligations organisationnelles.

### 1.8. Gestion du cycle de vie et assurance de sécurité

Le niveau de risque d'une intégration MCP peut évoluer à la suite d'une modification de ses fonctionnalités, de ses privilèges, de ses dépendances, de ses sources de données ou de son environnement d'exécution.

Une évaluation ponctuelle lors de l'introduction d'un serveur ne suffit donc pas à garantir le maintien de son niveau de sécurité.

Les mécanismes de gouvernance doivent couvrir l'ensemble du cycle de vie, depuis l'introduction et l'autorisation initiale jusqu'aux changements, aux réévaluations périodiques et au retrait.

Une attention particulière doit être accordée aux serveurs déjà en production, afin d'établir leur niveau de conformité et de traiter les risques identifiés selon leur criticité.

## 2. Recommandations de sécurité

### 2.1. Établir un cadre de gouvernance organisationnel

Il est recommandé de définir un cadre de gouvernance applicable à l'ensemble des serveurs MCP utilisés au sein de l'organisation, indépendamment de leur origine, de leur mode d'hébergement ou de leur environnement d'exécution.

Ce cadre devrait préciser les responsabilités des différentes parties prenantes, les conditions d'introduction et d'utilisation des serveurs, ainsi que les mécanismes de supervision et de gestion des risques.

L'autorisation d'une intégration MCP devrait reposer sur une évaluation documentée associant les responsabilités métier, d'architecture et de sécurité, conformément aux délégations d'autorité de l'organisation.

### 2.2. Mettre en place un inventaire centralisé

Il est recommandé d'établir et de maintenir un inventaire des serveurs MCP autorisés et utilisés.

Cet inventaire devrait permettre d'identifier au minimum le propriétaire, le fournisseur, l'environnement d'hébergement, les applications clientes, les capacités exposées, les systèmes et données accessibles, les identités utilisées et le statut d'autorisation.

Les mécanismes d'inventaire devraient également permettre de détecter les serveurs non déclarés ou non autorisés.

### 2.3. Instaurer une évaluation des risques proportionnée

Il est recommandé de soumettre chaque nouvelle intégration MCP à une évaluation des risques avant son utilisation en production.

Cette évaluation devrait notamment considérer la sensibilité des données accessibles, les privilèges accordés, les capacités d'action, l'exposition réseau, les dépendances externes et la criticité des systèmes concernés.

Une classification graduée des risques pourrait être adoptée, sous réserve de son alignement avec les méthodes de gestion des risques existantes.

Le niveau d'assurance attendu devrait être proportionnel au risque, avec une revue indépendante pour les intégrations présentant des enjeux de sécurité significatifs.

### 2.4. Encadrer les identités et les autorisations

Il est recommandé d'exiger l'application du principe du moindre privilège aux identités, aux serveurs et aux outils MCP.

Les mécanismes d'authentification et d'autorisation devraient être adaptés au contexte d'utilisation et permettre de limiter les accès aux ressources strictement nécessaires.

L'utilisation d'identités techniques devrait être encadrée, justifiée et traçable. Les secrets et jetons d'accès devraient faire l'objet de mesures de protection appropriées.

Les autorisations devraient être révisées périodiquement et lors de changements significatifs.

### 2.5. Encadrer les accès aux données et les flux externes

Il est recommandé de soumettre les accès aux données organisationnelles aux exigences de classification et de protection de l'information applicables.

Les flux de données entre les clients IA, les serveurs MCP et les services externes devraient être identifiés, documentés et autorisés en fonction de leur finalité.

Des restrictions adaptées devraient être appliquées afin de prévenir les accès excessifs, les transferts non autorisés et l'exposition de données sensibles.

### 2.6. Renforcer l'assurance des serveurs et outils MCP

Il est recommandé de prévoir des mécanismes d'assurance couvrant la provenance et l'intégrité des serveurs MCP, de leurs dépendances et des outils exposés.

Les contrôles devraient notamment tenir compte des risques de prompt injection, de tool poisoning, de compromission de la chaîne d'approvisionnement et d'exécution non autorisée.

Les mesures attendues devraient inclure, selon les risques, la validation des composants et des interfaces, l'isolation des environnements d'exécution, la limitation des privilèges et la surveillance des comportements anormaux.

Les modifications significatives des outils, de leurs descriptions ou de leurs capacités devraient faire l'objet d'une réévaluation appropriée.

### 2.7. Encadrer les fournisseurs tiers

Il est recommandé de limiter l'utilisation des serveurs MCP tiers aux fournisseurs préalablement approuvés conformément aux processus organisationnels applicables.

L'approbation d'un fournisseur devrait être complétée par une évaluation de chaque intégration envisagée, tenant compte des données accessibles, des capacités exposées et des conditions de traitement de l'information.

Les exigences contractuelles, les garanties de sécurité et les mécanismes de surveillance devraient être proportionnés à la criticité du service.

### 2.8. Assurer la traçabilité et la surveillance

Il est recommandé de mettre en œuvre des capacités de journalisation permettant de retracer les interactions MCP, les appels d'outils, les décisions d'autorisation et les opérations réalisées.

L'objectif devrait être de disposer d'une traçabilité suffisante pour soutenir les besoins d'audit, de détection et d'investigation.

Lorsque la conservation du contenu intégral des requêtes et réponses est nécessaire, elle devrait être encadrée par des mesures appropriées de classification, de contrôle d'accès, de protection des secrets, de rétention et de suppression.

Des mécanismes de surveillance devraient permettre d'identifier les comportements anormaux, les utilisations non autorisées et les tentatives de contournement des contrôles.

### 2.9. Formaliser la gestion des changements et des exceptions

Il est recommandé d'intégrer les serveurs MCP aux processus organisationnels de gestion des changements, des vulnérabilités et des incidents de sécurité.

Les changements susceptibles de modifier le niveau de risque d'une intégration devraient entraîner une réévaluation appropriée.

Les situations de non-conformité devraient être traitées selon leur niveau de risque, au moyen de restrictions d'utilisation, de plans de remédiation, d'exceptions formelles ou du retrait du serveur concerné.

Toute acceptation de risque résiduel devrait être documentée, limitée dans le temps lorsque pertinent, et approuvée par le propriétaire du risque disposant de l'autorité requise.

### 2.10. Réévaluer les serveurs existants et assurer une surveillance continue

Il est recommandé d'engager une démarche de régularisation des serveurs MCP déjà utilisés en production.

Cette démarche devrait comprendre leur recensement, l'identification de leurs propriétaires, l'évaluation de leurs risques et la définition de mesures correctives lorsque nécessaire.

Une période transitoire devrait permettre une mise en conformité progressive, avec une priorisation fondée sur les risques et des échéances documentées.

Par la suite, les intégrations MCP devraient faire l'objet de réévaluations périodiques selon leur criticité et lors de changements significatifs.

La deuxième ligne de défense devrait assurer une surveillance indépendante de l'application du cadre et produire, selon les mécanismes de gouvernance existants, une visibilité sur les risques, les exceptions et les écarts de conformité.

**Position de sécurité proposée**

L'utilisation des serveurs MCP au sein de l'organisation peut être autorisée sous réserve de l'établissement de responsabilités clairement définies, d'une évaluation proportionnée des risques et du respect des exigences minimales de sécurité applicables.

Cette autorisation doit porter sur le contexte d'intégration et d'utilisation du serveur, et non uniquement sur le composant logiciel ou son fournisseur.

La poursuite de l'utilisation des serveurs existants devrait être conditionnée à leur recensement, à leur évaluation et au traitement approprié des risques identifiés, conformément aux autorités décisionnelles et aux processus organisationnels applicables.
