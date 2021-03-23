---
title: ecr
description: 
published: true
date: 2021-03-23T16:29:07.935Z
tags: aws, cloud, containers, ecr
editor: markdown
dateCreated: 2021-03-08T11:38:32.170Z
---

# ECR
## Cos'è Amazon Elastic Container Registry?

Amazon Elastic Container Registry (Amazon ECR) è un servizio di registro di immagini del contenitore gestito da AWS che è sicuro, scalabile e affidabile. Amazon ECR supporta repository di immagini di container privati ​​con autorizzazioni basate sulle risorse utilizzando AWS IAM. In questo modo gli utenti specificati o le istanze Amazon EC2 possono accedere ai repository e alle immagini del container. Puoi utilizzare la tua CLI preferita per eseguire il push, il pull e la gestione di immagini Docker, immagini Open Container Initiative (OCI) e artefatti compatibili con OCI.


Il team dei servizi di container AWS mantiene una roadmap pubblica su GitHub. Contiene informazioni su ciò su cui stanno lavorando i team e consente a tutti i clienti AWS di fornire un feedback diretto. Per ulteriori informazioni, consulta Roadmap dei contenitori AWS.

## Componenti di Amazon ECR
Amazon ECR contiene i seguenti componenti:

### Registro
Un registro Amazon ECR viene fornito a ciascun account AWS; puoi creare archivi di immagini nel tuo registro e archiviarci le immagini.

#### Authorization token
Il tuo client deve autenticarsi nei registri di Amazon ECR come utente AWS prima di poter eseguire il push e il pull delle immagini.

#### Repository
Un repository di immagini Amazon ECR contiene le immagini Docker, le immagini OCI (Open Container Initiative) e gli elementi compatibili con OCI.

#### Repository policy
Puoi controllare l'accesso ai tuoi repository e alle immagini al loro interno con le policy del repository.

#### Immagine
Puoi eseguire il push e il pull delle immagini del contenitore nei tuoi repository. Puoi utilizzare queste immagini localmente sul tuo sistema di sviluppo oppure puoi utilizzarle nelle definizioni delle attività di Amazon ECS e nelle specifiche dei pod di Amazon EKS.

## Caratteristiche di Amazon ECR
Amazon ECR fornisce le seguenti funzionalità:

- Le policy del ciclo di vita aiutano a gestire il ciclo di vita delle immagini nei tuoi repository. Si definiscono le regole che comportano la pulizia delle immagini inutilizzate. Puoi testare le regole prima di applicarle al tuo repository. Per ulteriori informazioni, vedere Criteri del ciclo di vita .

- La scansione delle immagini aiuta a identificare le vulnerabilità del software nelle immagini del contenitore. Ogni repository può essere configurato per eseguire la scansione su push . Ciò garantisce che ogni nuova immagine inviata al repository venga sottoposta a scansione. È quindi possibile recuperare i risultati della scansione dell'immagine. Per ulteriori informazioni, vedere Scansione di immagini .

- La replica su più regioni e su più account ti consente di avere più facilmente le tue immagini dove ne hai bisogno. Questa è configurata come un'impostazione del Registro di sistema ed è per regione. Per ulteriori informazioni, vedere Impostazioni del registro privato .


## References
- https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html