---
title: Scribe
description: Scribe introduction
published: true
date: 2020-02-25T15:45:08.990Z
tags: 
---

# **TIBCO Scribe® Online**

## Introduzione

**Risorse**: https://integration.cloud.tibco.com/docs/scribe/

TIBCO Scribe® Online è una funzionalità di TIBCO Cloud ™ che consente agli sviluppatori di creare integrazioni tra qualsiasi combinazione di applicazioni basate su cloud e on-premise. 
E' costituito da un motore di integrazione di base e dai seguenti componenti:
- **Connector**: deputati allo spostamento dei dati tra applicazioni;
- **Solution**: insiemi di opzioni di configurazione specificate dall'utente che TIBCO Scribe® Online utilizza per eseguire un'attività specifica. Le solutions contengono un agente, istruzioni di mappatura e informazioni sulla connessione;
- **TIBCO Scribe® Online Agent**: favorisce comunicazioni sicure tra le fonti di dati utilizzate da una solution;
- **Map**: è una rappresentazione visiva delle istruzioni necessarie per integrare i dati.

### Connector
Un Connector è un software utilizzato per spostare i dati tra applicazioni specifiche utilizzando le API di tali applicazioni. 
Una Connection è la configurazione dei parametri richiesti dal connettore per connettersi all'archivio dati di un'applicazione specifica.
TIBCO Scribe® Online mette a disposizione una lista di connettori da poter installare. Per installare un connettore è sufficiente recarsi nella sezione _Maketplace_, scegliere il connettore dalla lista di quelli disponibili e cliccare su _Install_.
![marketplace.png.png](/scribe/marketplace.png.png)

Una volta installato, il connettore sarà disponibile nella sezione _Dashboard_ > _Connection_.
![dash_connection.png](/scribe/dash_connection.png)

La pagina delle connessioni visualizza lo stato delle Connections utilizzate dall'organizzazione corrente.
Per creare una Connection, sfruttando il Connector precedentemente installato, è necessario selezionare il tasto **+** della sezione Connection e infine scegliere il _Connector Type_.
![add_connection.png](/scribe/add_connection.png)

### Solution
Una Solution è un insieme di opzioni di configurazione specificate dall'utente che TIBCO Scribe® Online utilizza per eseguire un'attività specifica.

Le Solutions contengono i seguenti oggetti, che co-operano tra loro al fine di eseguire un'attività:
1. un agente;
2. istruzioni di mappatura;
3. informazioni sulla connessione. 

Un'organization supporta 3 tippologie di Solutions:

- **Replication Services (RS) Solutions**: utilizzati per copiare dati da una sorgente ad un'altra;
- **Integration Services (IS) Solutions**: utilizzati per integrare i dati da un'origine dati a una o più origini dati di destinazione. Le soluzioni IS utilizzano Mappe, Filtri e Formule per manipolare i dati mentre in spostamento da un'origine dati a un'altra. 
Esistono due tipi di soluzioni di integrazione, dette soluzioni pianificate ed eventi;
- **Migration Services (MS) Solutions**: utilizzati per migrare i dati da un archivio dati a un altro.

Per creare una nuova Solution, selezionare il tasto **+** e il tipo _Solution Service_ desiderato.
![solution.png](/scribe/solution.png)

### TIBCO Scribe® Online Agent
TIBCO Scribe® Online Agent facilita la comunicazione tra le fonti di dati utilizzate da una soluzione. È necessario un agente per comunicare con i dati di origine e di destinazione e con TIBCO Scribe® Online nel cloud.

Sono disponibili due tipi di agenti:

- **On-Premise Agent**: è installabile su un computer direttamente dal sito web. È possibile installare più agenti locali su un singolo computer.
- **Cloud Agent**: risiede nel cloud nel data center associato alla tua organizzazione. È possibile eseguire il provisioning di un solo agente cloud per organizzazione.

La determinazione del tipo di agente da selezionare varia in base al connettore utilizzato e alla posizione dei dati a cui si accede, sia in locale che in cloud.
L'On-Premise Agent può essere utilizzato in soluzioni con qualsiasi connessione e con archivi dati sia cloud che locali.
Il Cloud Agent può essere utilizzato solo quando tutte le connessioni in una soluzione e gli archivi dati associati supportano l'agente cloud.
![cloud_agent.png](/scribe/cloud_agent.png)

### Maps
Una mappa è una rappresentazione visiva delle istruzioni necessarie per integrare i dati. 
Set di una o più mappe sono utilizzate nelle soluzioni di integrazione e migrazione per recuperare e manipolare i dati. Le soluzioni di replica non utilizzano Maps perché copiano semplicemente i dati da un'origine dati a un'altra.

TIBCO Scribe® Online offre la possibilità di creare mappe per eseguire attività specifiche. I tipi di mappe sono:

1. **Integration Map**: integra i dati da una sorgente a uno o più datastores.
2. **Message Map**: elabora le modifiche in tempo reale da un messaggio in uscita di Salesforce a uno o più datastores di destinazione.
3. **Request/Reply Map**: Un'interfaccia aperta utilizzata per integrare TIBCO Scribe® Online Maps nel tuo prodotto software. E' necessario definire un servizio Web che funge da fonte. Il codice sviluppato può utilizzare la richiesta del Web service per integrare i dati in uno o più datastores di destinazione.

Quando si creano mappe, la pagina _Create Map_ si apre nello spazio di lavoro vuoto. 
Utilizzando il pannello _Add Connection_ si può selezionare una o più connessioni. Per ogni connessione, esistono una serie di blocchi operativi che è possibile utilizzare per elaborare i dati per quella connessione.
![map.png](/scribe/map.png)

Le schede sul lato destro dell'area di lavoro forniscono ulteriori informazioni sul blocco selezionato o sulla mappa, come:
- **Properties**: visualizza le proprietà associate al blocco selezionato.
- **Errors, Warnings**: visualizza un elenco di errori e avvisi per la mappa.
- **Find & Replace**: utilizzata per aggiornare il testo nei _Map Blocks_.

## Use case livello base
### Obiettivo
Lo scopo di questa sezione è creare una semplice Integration Solution che recuperi il contenuto di un file Dropbox e usi tale contenuto per invocare un'API REST.
Gli elementi e i passaggi necessari allo sviluppo dell'esercizio sono i seguenti:
1. File in formato .csv situato nella Home di Dropbox, contenente le seguente informazioni

sku|product_type|erp|etichetta|image
---|---|---|---|---
102004|all|true|true|true
102016|all|true|true|true
2. Base URI e Specification del REST Web Service (swagger)

### Implementazione esercizio
#### Creazione delle Connections
**Prerequisiti**
E' necessario aver installato dal _Marketplace_ i seguenti Connectors:
- Text File as a Source
- Rest Web Services
##### Text File as a Source Connection
Nella pagina _Dashboard_, creare una nuova Connection selezionando il tasto + _Add New Connection_. 
All'interno della sezione di configurazione della nuova Connection:
- selezionare come _Connector Type_ la voce _Text File as a Source_
- nel tab _Location_, selezionare _Dropbox_ come _File Location_. In seguito autenticarsi ed eseguire la validazione
![connection_location.png](/scribe/connection_location.png)
- nel tab _Entities_ configurare i campi _Entity Name_, _File Name_, _Field Delimiter_
![connection_entities.png](/scribe/connection_entities.png)
- nel tab Fields selezionare la voce _Generate fileds schema from your data_ e salvare
##### Rest Web Services Connection
Nella pagina _Dashboard_, creare una nuova Connection selezionando il tasto + _Add New Connection_. 
All'interno della sezione di configurazione della nuova Connection:
- selezionare come _Connector Type_ la voce _Rest Web Services_
- nel tab _Specification_, inserire i seguenti parametri:
    * Base URI: https://venchi.api.mashery.com
    * Specification: inserire lo swagger del serizio Rest
<div style="overflow-y: scroll; height: 400px;"><pre>
{ "swagger": "2.0",
    "info": {
        "version": "1.0",
        "title": "Masterdata Product",
        "description": "__APIs inventory to integrate Venchi and Akeneo PIM__"
    },
    "host": "venchi.api.mashery.com",
    "basePath": "/masterdata/v1",
    "schemes": [
        "https"
    ],
    "securityDefinitions": {
        "ApiKeyAuth": {
            "type": "apiKey",
            "in": "header",
            "name": "api_key"
        }
    },
    "security": [
        {
            "ApiKeyAuth": []
        }
    ],
    "paths": {
        "/products/erp-to-pim": {
            "post": {
                "summary": "Upload products from ERP to PIM",
                "description": "__Upload products on PIM__",
                "operationId": "post-product-erptopim",
                "consumes": [
                    "application/json"
                ],
                "produces": [
                    "application/json"
                ],
                "parameters": [
                    {
                        "name": "body",
                        "in": "body",
                        "description": "",
                        "schema": {
                            "$ref": "#/definitions/productPim"
                        },
                        "required": true
                    }
                ],
                "responses": {
                    "200": {
                        "description": "OK",
                        "schema": {
                            "$ref": "#/definitions/productResponse"
                        }
                    },
                    "500": {
                        "description": "Internal Server Error",
                        "schema": {
                            "$ref": "#/definitions/productResponse"
                        }
                    }
                }
            }
        },
        "/products/pim-to-channels": {
            "post": {
                "consumes": [
                    "application/json"
                ],
                "description": "",
                "operationId": "post-product-pimtochannels",
                "parameters": [
                    {
                        "description": "__Upload PIM products to eCommerce/Amazon channels__",
                        "in": "body",
                        "name": "body",
                        "required": true,
                        "schema": {
                            "$ref": "#/definitions/channelRequest"
                        }
                    }
                ],
                "produces": [
                    "application/json"
                ],
                "responses": {
                    "200": {
                        "description": "OK",
                        "schema": {
                            "$ref": "#/definitions/channelsResponse"
                        }
                    },
                    "500": {
                        "description": "Internal Server Error",
                        "schema": {
                            "$ref": "#/definitions/productResponse"
                        }
                    }
                },
                "summary": "Upload PIM products to eCommerce/Amazon channels"
            }
        }
    },
    "definitions": {
        "productPim": {
            "type": "object",
            "properties": {
                "filters": {
                    "$ref": "#/definitions/productFilters"
                },
                "routing": {
                    "$ref": "#/definitions/productRouting"
                },
                "enrichment": {
                    "$ref": "#/definitions/productEnrichment"
                }
            }
        },
        "productRouting": {
            "type": "object",
            "properties": {
                "transfer_type": {
                    "type": "string"
                },
                "erp": {
                    "type": "boolean"
                },
                "etichetta": {
                    "type": "boolean"
                },
                "image": {
                    "type": "boolean"
                }
            }
        },
        "productEnrichment": {
            "type": "object",
            "properties": {
                "gruppo_statistico_2": {
                    "type": "string"
                },
                "gruppo_statistico_3": {
                    "type": "string"
                },
                "data_attivazione_canale": {
                    "$ref": "#/definitions/data_attivazione_canale"
                },
                "data_disattivazione_canale": {
                    "$ref": "#/definitions/data_disattivazione_canale"
                }
            }
        },
        "productResponse": {
            "type": "object",
            "properties": {
                "status": {
                    "type": "string"
                },
                "message": {
                    "type": "string"
                }
            }
        },
        "data_disattivazione_canale": {
            "type": "object",
            "properties": {
                "ecommerce": {
                    "type": "string",
                    "format": "date"
                },
                "amazon": {
                    "type": "string",
                    "format": "date"
                }
            }
        },
        "productFilters": {
            "type": "object",
            "properties": {
                "skus": {
                    "type": "array",
                    "items": {
                        "type": "string",
                        "uniqueItems": false
                    }
                },
                "eans": {
                    "type": "array",
                    "items": {
                        "type": "string",
                        "uniqueItems": false
                    }
                },
                "famiglia": {
                    "type": "string"
                },
                "sottofamiglia": {
                    "type": "string"
                },
                "campagna": {
                    "type": "string"
                },
                "anno": {
                    "type": "integer"
                },
                "stato": {
                    "type": "string"
                },
                "stato_integrazione": {
                    "type": "string"
                },
                "product_type": {
                    "type": "string"
                }
            }
        },
        "data_attivazione_canale": {
            "type": "object",
            "properties": {
                "ecommerce": {
                    "type": "string",
                    "format": "date"
                },
                "amazon": {
                    "type": "string",
                    "format": "date"
                }
            }
        },
        "channelRequest": {
            "properties": {
                "enrichment": {
                    "$ref": "#/definitions/channelEnrichment"
                },
                "filters": {
                    "$ref": "#/definitions/channelFilters"
                },
                "routing": {
                    "$ref": "#/definitions/channelRouting"
                }
            },
            "type": "object"
        },
        "channelsResponse": {
            "properties": {
                "message": {
                    "type": "string"
                },
                "status": {
                    "type": "string"
                }
            },
            "required": [
                "message",
                "status"
            ],
            "type": "object"
        },
        "channelEnrichment": {
            "properties": {
                "data_attivazione_canale": {
                    "format": "date",
                    "type": "string"
                },
                "data_disattivazione_canale": {
                    "format": "date",
                    "type": "string"
                }
            },
            "type": "object"
        },
        "channelFilters": {
            "properties": {
                "anno": {
                    "type": "integer"
                },
                "campagna": {
                    "type": "string"
                },
                "categories": {
                    "items": {
                        "type": "string",
                        "uniqueItems": false
                    },
                    "type": "array"
                },
                "skus": {
                    "items": {
                        "type": "string",
                        "uniqueItems": false
                    },
                    "type": "array"
                },
                "stato": {
                    "type": "string"
                }
            },
            "type": "object"
        },
        "channelRouting": {
            "properties": {
                "channels": {
                    "items": {
                        "type": "string",
                        "uniqueItems": false
                    },
                    "type": "array"
                }
            },
            "type": "object"
        }
    }
}</pre></div>

- nel tab _Authorization_ fornire le specifiche di autenticazione dell'API Rest
![restconn_auth.png](/scribe/restconn_auth.png)

#### Creazione di una Solution
**Prerequisiti**
Aver precedentemente configurato una o più Connections.

Questa esercitazione ha come scopo quello di creare un Integration Service, pertanto la _Solution_ che implementeremo sarà di tipo _Integration_. 
Nella sezione _Solution_ selezionare il tasto + > _Integration_ per creare la nuova IS.
Come detto in precedenza, una Solution è caratterizzata da una _Map_, ovvero la rappresentazione grafica del servizio di integrazione sviluppato. Quindi per definire una Solution è necessario configurare una Map.

##### Configurazione di una Map
All'interno della sezione _Map_ della nuova Solution creata, selezionare il simbolo in alto a destra e selezionare _Create Integration Map_.
![add_map_sol.png](/scribe/add_map_sol.png)
Per poter sviluppare graficamente il servizio di integrazione, è necessario aggiungere le Connenctions precedentemente configurate, in quanto le operazioni permesse (_Map Blocks_) dipendono strettamente dal tipo di connection impostata. 
Per aggiungere una Connection ad una Map selezionare la voce _Add Connection_ e scegliere dal menù a tendina le due Connections precedentemente configurate (Text File as a Source, Rest Web Services)
![add_map_conn.png](/scribe/add_map_conn.png)

##### Sviluppo grafico
Riprendendo l'obiettivo del IS, i passi da seguire per lo sviluppo sono:
1. Leggere i dati dal file presente su Dropbox: possiamo utilizzare il Map Block _Query_ e configurare l'entità. Nella sezione _Preview_ è presente l'anteprima del contenuto del file.
![query.png](/scribe/query.png)
2. Per ogni riga del file, andremo ad invocare l'API Rest. Pertanto eseguiremo un _For Eeach Result_ e invocheremo una _Post_
![foreach.png](/scribe/foreach.png)
3. Configurazione del servizio Rest: 
    * Nel tab _General_ configurare il campo _Entity_ con l'endpoint da invocare (e.g. post_productserptopim)
    ![general_rest.png](/scribe/general_rest.png)
    * Nel tab _Include_ è possibile selezionare gli elementi della request definiti nello swagger, che si vogliono utilizzare e valorizzare. In questo caso sceglieremo _productFilters_ e _productRouting_
    ![include_rest.png](/scribe/include_rest.png)
    * Nel tab _Fields_ è possibile eseguire il mapping tra i parametri di input presenti nel file Dropbox e la request dell'API Rest. In questo caso il mapping è molto intuitivo in quanto i parametri presentano la stessa naming sia sul file di input che nella request dell'API
    ![fields_rest.png](/scribe/fields_rest.png)

##### Run Solution
Una volta terminato lo sviluppo grafico, è possibile eseguire la configurazione della Solution creata, selezionando l'opzione **RUN** nella sezione _Integration_.
![run_map.png](/scribe/run_map.png)
Una volta terminata l'esecuzione è possibile prendere visione dei risultati nella sezione _Execution History_
![execution_history.png](/scribe/execution_history.png)

Selezionando la voce _Status_ è possibile ispezionare il dettaglio dell'esecuzione e analizzare gli eventuali errori/warnings.
![history_details.png](/scribe/history_details.png)

## Use case livello avanzato