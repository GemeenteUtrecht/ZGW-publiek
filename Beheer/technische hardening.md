# Checklist Technische & Functionele hardening Proeftuin infrastructuur

Deze lijst bevat alle acties die op dit moment moeten gebeuren voor er live/in productie
kan gegaan worden. Er zijn vast nog items vergeten, maar deze worden aangevuld zodra
ze te binnen schieten.

De aandachtspunten zouden de verantwoordelijkheid worden van DevOps, op dit moment een hypothetische rol die nog _niet_ bestaat binnen GU.

## Infrastructuur

- [ ] Productiecluster geïsoleerd van proeftuincluster (Cyso)
- [ ] Whitelist IP-adressen jump-host opstellen en doorgeven aan Cyso (Utrecht)
- [ ] Backupstrategie
    - [ ] Point-in-time recovery van PostgreSQL en MySQL databases of (Cyso)
    - [ ] Opstellen en implementeren van retention policy (Utrecht & Cyso)
    - [ ] Het (automatisch) testen van disaster recovery (Cyso)
    - [ ] Backups van Alfresco database & filesystem op host (buiten K8s cluster) (Cyso / Contezza?)
    - [ ] Testen disaster recovery Alfresco (Cyso / Contezza)
    - [ ] Backup & recovery van persistent volume data in het cluster (Cyso)
    - [ ] Wat met verstuurde notificaties (timestamp _na_ backup restore) -> replay omgekeerde actie in omgekeerde volgorde? (Utrecht)
    - [ ] Uitzoeken: wat met Alfresco index rebuild? (Utrecht / Contezza)
- [ ] Het encrypten van de data in de database - encryption at rest (Cyso)
- [ ] DNS control utrecht.nl / inrichten subdomeinen voor apps (Utrecht)
- [ ] SSL certificaten - verschillende validationniveaus, hoe verkrijgen, hoe beheren... (Utrecht)
- [ ] Monitoring: uptimerobot of vergelijkbaar, monitor ook SSL (Utrecht)
- [ ] SSL strength test - Qualys https://www.ssllabs.com/ssltest/ (Utrecht / leverancier applicatie)
- [ ] Credentials & connectieparameters voor Utrecht mailserver om uitgaande e-mail te
      kunnen versturen. (Utrecht aanleveren aan leveranciers / devops)
- [ ] Aanmaken van applicatie in ADFS en opvoeren van geldige callback URLs (Utrecht IAM)
- [ ] Sentry-error-monitoring omgeving (afnemen in cloud of self-hosted) (Utrecht)
- [ ] Applicatie-monitoring in Sentry (Utrecht / leverancier)
- [ ] Applicatie-performance monitoring met Elastic APM en/of Newrelic? (leverancier)
- [ ] PKI overheid certificaat voor NLX inway/outway - productie (Utrecht)
- [ ] Op NLX inway configureren welke organisaties bij services mogen komen (Utrecht)
- [ ] Monitoring op Camunda incidents. Deze kunnen getriggered worden door crashende
      BPTL taken, bijvoorbeeld als een achterliggende service niet bereikbaar is. (Utrecht / FB)
- [ ] Monitoring op de database (Cyso)
    - [ ] Number of connections vs. connection limit (100)
    - [ ] Slow query log?
- [ ] Onderzoek optie connection pooling naar database, vb. pgBouncer (Sergei)
- [ ] multi-replica Camunda - breekt nu login/sessies! (Sergei)
- [ ] Technische service processen & incident management inrichten (Utrecht)

## Documentatie

- [ ] Documenteer hoe de deployment/infrastructuur code werkt (Sergei)
- [ ] Verzamel documentatie-entrypoints van gedeployde applicaties (Sergei)
- [ ] Documenteer applicaties zelf (Sergei / leverancier)
    - [ ] Camunda
    - [ ] BPTL
    - [ ] ZAC

## Audit/access control

- [ ] Inventaris van wie toegang heeft tot welke cluster en op welke wijze (Utrecht / Cyso)
- [ ] Audit trail van operaties in het cluster - weten wie wanneer een deploy aangepast
      heeft. (Cyso)
- [ ] Toegang beheren tot dashboards Cyso (Utrecht / Cyso)
- [ ] Voorkom single point of failure: meer mensen moeten de infrastructuur snappen en
      kunnen beheren. (Utrecht)
- [ ] Aanmaken (API) accounts in Camunda met correcte rechten (Utrecht / FB)
- [ ] Aanmaken en instellen van superusers in de applicaties (Utrecht / FB)
- [ ] organiseren pentests (bij voorkeur extern) (Utrecht)
- [ ] Password policy op servers - pubkey only SSH (Cyso)

## Abonemmenten/licenties

- [ ] Kadaster kondigde aan de (nieuwe versies van?) API's betalend te gaan maken (Utrecht)

## Functionele hardening (FB)

- acceptatie van features
- performance
- beheersbaarheid
- functionele documentatie
- privacy
- functionele security
