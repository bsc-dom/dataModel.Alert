Entidad: Anomalía  
=================  
[Licencia abierta](https://github.com/smart-data-models//dataModel.Alert/blob/master/Anomaly/LICENSE.md)  
Descripción global: **Esta entidad contiene una descripción armonizada de una anomalía.**  

## Lista de propiedades  

- `address`: La dirección postal  - `alternateName`: Un nombre alternativo para este artículo  - `anomalousProperty`: La controlledProperty (del dispositivo) en la que se detectó la anomalía  - `areaServed`: La zona geográfica en la que se presta un servicio o se ofrece un artículo  - `dataProvider`: Una secuencia de caracteres que identifica al proveedor de la entidad de datos armonizada.  - `dateCreated`: Marca de tiempo de creación de la entidad. Suele ser asignada por la plataforma de almacenamiento.  - `dateDetected`: La fecha y hora en que se detectó la anomalía por primera vez  - `dateModified`: Marca de tiempo de la última modificación de la entidad. Normalmente será asignada por la plataforma de almacenamiento.  - `description`: Una descripción de este artículo  - `detectedBy`: El ID del dispositivo en el que se ha detectado la anomalía  - `id`: Identificador único de la entidad  - `location`:   - `name`: El nombre de este artículo.  - `owner`: Una lista que contiene una secuencia de caracteres codificada en JSON que hace referencia a los identificadores únicos de los propietarios  - `seeAlso`: lista de uri que apuntan a recursos adicionales sobre el artículo  - `source`: Una secuencia de caracteres que indica la fuente original de los datos de la entidad en forma de URL. Se recomienda que sea el nombre de dominio completo del proveedor de origen, o la URL del objeto de origen.  - `thresholdBreach`: Descripción de un incumplimiento del umbral observado que contribuyó a la detección de una anomalía  - `type`: Tipo de entidad NGSI-LD. Tiene que ser Anomalía    
Propiedades requeridas  
- `anomalousProperty`  - `dateDetected`  - `id`  - `type`  ## Descripción del modelo de datos de las propiedades  
Ordenados alfabéticamente (haga clic para ver los detalles)  
<details><summary><strong>full yaml details</strong></summary>    
```yaml  
Anomaly:    
  description: 'This entity contains a harmonised description of an anomaly.'    
  properties:    
    address:    
      description: 'The mailing address'    
      properties:    
        addressCountry:    
          description: 'Property. The country. For example, Spain. Model:''https://schema.org/addressCountry'''    
          type: string    
        addressLocality:    
          description: 'Property. The locality in which the street address is, and which is in the region. Model:''https://schema.org/addressLocality'''    
          type: string    
        addressRegion:    
          description: 'Property. The region in which the locality is, and which is in the country. Model:''https://schema.org/addressRegion'''    
          type: string    
        areaServed:    
          description: 'Property. The geographic area where a service or offered item is provided. Model:''https://schema.org/areaServed'''    
          type: string    
        postOfficeBoxNumber:    
          description: 'Property. The post office box number for PO box addresses. For example, Spain. Model:''https://schema.org/postOfficeBoxNumber'''    
          type: string    
        postalCode:    
          description: 'Property. The postal code. For example, Spain. Model:''https://schema.org/https://schema.org/postalCode'''    
          type: string    
        streetAddress:    
          description: 'Property. The street address. Model:''https://schema.org/streetAddress'''    
          type: string    
      type: Property    
      x-ngsi:    
        model: https://schema.org/adddress    
    alternateName:    
      description: 'An alternative name for this item'    
      type: Property    
    anomalousProperty:    
      description: 'The controlledProperty (of the device) in which the anomaly was detected'    
      type: Property    
      x-ngsi:    
        model: http://schema.org/Text    
    areaServed:    
      description: 'The geographic area where a service or offered item is provided'    
      type: Property    
      x-ngsi:    
        model: https://schema.org/Text    
    dataProvider:    
      description: 'A sequence of characters identifying the provider of the harmonised data entity.'    
      type: Property    
    dateCreated:    
      description: 'Entity creation timestamp. This will usually be allocated by the storage platform.'    
      format: date-time    
      type: Property    
    dateDetected:    
      description: 'The date and time at which the anomaly was first detected'    
      type: Property    
      x-ngsi:    
        model: http://schema.org/DateTime    
    dateModified:    
      description: 'Timestamp of the last modification of the entity. This will usually be allocated by the storage platform.'    
      format: date-time    
      type: Property    
    description:    
      description: 'A description of this item'    
      type: Property    
    detectedBy:    
      description: 'The ID of the device at which the anomaly was detected'    
      format: uri    
      type: Relationship    
    id:    
      anyOf: &anomaly_-_properties_-_owner_-_items_-_anyof    
        - description: 'Property. Identifier format of any NGSI entity'    
          maxLength: 256    
          minLength: 1    
          pattern: ^[\w\-\.\{\}\$\+\*\[\]`|~^@!,:\\]+$    
          type: string    
        - description: 'Property. Identifier format of any NGSI entity'    
          format: uri    
          type: string    
      description: 'Unique identifier of the entity'    
      type: Property    
    location:    
      $id: https://geojson.org/schema/Geometry.json    
      $schema: "http://json-schema.org/draft-07/schema#"    
      oneOf:    
        - properties:    
            bbox:    
              items:    
                type: number    
              minItems: 4    
              type: array    
            coordinates:    
              items:    
                type: number    
              minItems: 2    
              type: array    
            type:    
              enum:    
                - Point    
              type: string    
          required:    
            - type    
            - coordinates    
          title: 'GeoJSON Point'    
          type: object    
        - properties:    
            bbox:    
              items:    
                type: number    
              minItems: 4    
              type: array    
            coordinates:    
              items:    
                items:    
                  type: number    
                minItems: 2    
                type: array    
              minItems: 2    
              type: array    
            type:    
              enum:    
                - LineString    
              type: string    
          required:    
            - type    
            - coordinates    
          title: 'GeoJSON LineString'    
          type: object    
        - properties:    
            bbox:    
              items:    
                type: number    
              minItems: 4    
              type: array    
            coordinates:    
              items:    
                items:    
                  items:    
                    type: number    
                  minItems: 2    
                  type: array    
                minItems: 4    
                type: array    
              type: array    
            type:    
              enum:    
                - Polygon    
              type: string    
          required:    
            - type    
            - coordinates    
          title: 'GeoJSON Polygon'    
          type: object    
        - properties:    
            bbox:    
              items:    
                type: number    
              minItems: 4    
              type: array    
            coordinates:    
              items:    
                items:    
                  type: number    
                minItems: 2    
                type: array    
              type: array    
            type:    
              enum:    
                - MultiPoint    
              type: string    
          required:    
            - type    
            - coordinates    
          title: 'GeoJSON MultiPoint'    
          type: object    
        - properties:    
            bbox:    
              items:    
                type: number    
              minItems: 4    
              type: array    
            coordinates:    
              items:    
                items:    
                  items:    
                    type: number    
                  minItems: 2    
                  type: array    
                minItems: 2    
                type: array    
              type: array    
            type:    
              enum:    
                - MultiLineString    
              type: string    
          required:    
            - type    
            - coordinates    
          title: 'GeoJSON MultiLineString'    
          type: object    
        - properties:    
            bbox:    
              items:    
                type: number    
              minItems: 4    
              type: array    
            coordinates:    
              items:    
                items:    
                  items:    
                    items:    
                      type: number    
                    minItems: 2    
                    type: array    
                  minItems: 4    
                  type: array    
                type: array    
              type: array    
            type:    
              enum:    
                - MultiPolygon    
              type: string    
          required:    
            - type    
            - coordinates    
          title: 'GeoJSON MultiPolygon'    
          type: object    
      title: 'GeoJSON Geometry'    
    name:    
      description: 'The name of this item.'    
      type: Property    
    owner:    
      description: 'A List containing a JSON encoded sequence of characters referencing the unique Ids of the owner(s)'    
      items:    
        anyOf: *anomaly_-_properties_-_owner_-_items_-_anyof    
        description: 'Property. Unique identifier of the entity'    
      type: Property    
    seeAlso:    
      description: 'list of uri pointing to additional resources about the item'    
      oneOf:    
        - items:    
            - format: uri    
              type: string    
          minItems: 1    
          type: array    
        - format: uri    
          type: string    
      type: Property    
    source:    
      description: 'A sequence of characters giving the original source of the entity data as a URL. Recommended to be the fully qualified domain name of the source provider, or the URL to the source object.'    
      type: Property    
    thresholdBreach:    
      description: 'Description of an observed threshold breach that contributed to detection of an anomaly'    
      properties:    
        dateObserved:    
          description: 'Property. Model:''http://schema.org/DateTime''. A sub-property of the Property ''thresholdBreach''. The date and time at which the threshold breach was observed'    
          type: string    
        measuredValue:    
          description: 'Property. Model:''http://schema.org/Number''. A sub-property of the Property ''thresholdBreach''. The value measured for the corresponding device and controlled property'    
          type: number    
        thresholdType:    
          description: 'Property. Model:''https://schema.org/Text''. A sub-property of the Property ''thresholdBreach''. The type of the threshold that was breached'    
          enum:    
            - UPPER    
            - LOWER    
          type: string    
        thresholdValue:    
          description: 'Property. Model:''https://schema.org/Number''. A sub-property of the Property ''thresholdBreach''. The value of the threshold that was breached'    
          type: number    
      type: Property    
      x-ngsi:    
        model: https://schema.org/Text    
    type:    
      description: 'NGSI-LD Entity Type. It has to be Anomaly'    
      enum:    
        - Anomaly    
      type: Property    
  required:    
    - id    
    - type    
    - anomalousProperty    
    - dateDetected    
  type: object    
```  
</details>    
## Ejemplo de carga útil  
#### Anomalía NGSI V2 key-values Ejemplo  
Aquí hay un ejemplo de una anomalía en formato JSON como valores-clave. Esto es compatible con NGSI V2 cuando se utiliza `options=keyValues` y devuelve los datos de contexto de una entidad individual.  
```json  
{  
  "id": "1863179e-3768-4480-9167-ff21f870dd19",  
  "type": "Anomaly",  
  "detectedBy": "urn:ngsi-ld:Device:1863179e-3868-4480-3496-jf21f090dd20",  
  "anomalousProperty": "Pressure",  
  "dateDetected": "2021-01-14T15:45:00Z",  
  "thresholdBreach": [  
    {  
      "dateObserved": "2021-01-14T15:30:00Z",  
      "measuredValue": "18.91",  
      "thresholdType": "LOWER",  
      "thresholdValue": "20"  
    },  
    {  
      "value": "2021-01-14T15:45:00Z",  
      "measuredValue": "18.91",  
      "thresholdType": "LOWER",  
      "thresholdValue": "20"  
    }  
  ]  
}  
```  
#### Anomalía NGSI V2 normalizada Ejemplo  
He aquí un ejemplo de una anomalía en formato JSON normalizado. Esto es compatible con NGSI V2 cuando no se utilizan opciones y devuelve los datos de contexto de una entidad individual.  
```json  
{  
    "id": "1863179e-3768-4480-9167-ff21f870dd19",  
    "type": "Anomaly",  
    "detectedBy": {  
        "type": "Relationship",  
        "object": "urn:ngsi-ld:Device:1863179e-3868-4480-3496-jf21f090dd20"  
    },  
    "anomalousProperty": {  
        "value": "Pressure"  
    },  
    "dateDetected": {  
        "value": "2021-01-14T15:45:00Z"  
    },  
    "thresholdBreach": [  
        {  
            "datasetId": "Breach1",  
            "value": {  
                "dateObserved": {  
                    "value": "2021-01-14T15:30:00Z"  
                },  
                "measuredValue": {  
                    "value": "18.91",  
                    "unitCode": "MTR"  
                },  
                "thresholdType": {  
                    "value": "LOWER"  
                },  
                "thresholdValue": {  
                    "value": "20",  
                    "unitCode": "MTR"  
                }  
            }          
        },  
        {  
            "datasetId": "Breach2",  
            "value": {  
                "dateObserved": {  
                    "value": "2021-01-14T15:45:00Z"  
                },  
                "measuredValue": {  
                    "value": "18.91",  
                    "unitCode": "MTR"  
                },  
                "thresholdType": {  
                    "value": "LOWER"  
                },  
                "thresholdValue": {  
                    "value": "20",  
                    "unitCode": "MTR"  
                }  
            }          
        }  
    ]  
}  
```  
#### Anomalía NGSI-LD key-values Ejemplo  
Aquí hay un ejemplo de una anomalía en formato JSON-LD como valores-clave. Esto es compatible con NGSI-LD cuando se utiliza `options=keyValues` y devuelve los datos de contexto de una entidad individual.  
```json  
{  
  "id": "1863179e-3768-4480-9167-ff21f870dd19",  
  "type": "Anomaly",  
  "detectedBy": "urn:ngsi-ld:Device:1863179e-3868-4480-3496-jf21f090dd20",  
  "anomalousProperty": "Pressure",  
  "dateDetected": "2021-01-14T15:45:00Z",  
  "thresholdBreach": [  
    {  
      "dateObserved": "2021-01-14T15:30:00Z",  
      "measuredValue": "18.91",  
      "thresholdType": "LOWER",  
      "thresholdValue": "20"  
    },  
    {  
      "value": "2021-01-14T15:45:00Z",  
      "measuredValue": "18.91",  
      "thresholdType": "LOWER",  
      "thresholdValue": "20"  
    }  
  ],  
  "@context": [  
    "https://schema.lab.fiware.org/ld/context"  
  ]  
}  
```  
#### Anomalía NGSI-LD normalizada Ejemplo  
He aquí un ejemplo de una anomalía en formato JSON-LD normalizado. Esto es compatible con NGSI-LD cuando no se utilizan opciones y devuelve los datos de contexto de una entidad individual.  
```json  
{  
    "id": "urn:ngsi-ld:Anomaly:1863179e-3768-4480-9167-ff21f870dd19",  
    "type": "Anomaly",  
    "createdAt": "2021-01-14T15:45:00Z",  
    "modifiedAt": "2021-01-14T15:45:00Z",  
    "detectedBy": {  
        "type": "Relationship",  
        "object": "urn:ngsi-ld:Device:1863179e-3868-4480-3496-jf21f090dd20"  
    },  
    "anomalousProperty": {  
        "type": "Property",  
        "value": "Pressure"  
    },  
    "dateDetected": {  
        "type": "Property",  
        "value": "2021-01-14T15:45:00Z"  
    },  
    "thresholdBreach": [  
        {  
            "datasetId": "urn:ngsi-ld:Dataset:Breach1",  
            "value": {  
                "dateObserved": {  
                    "type": "Property",  
                    "value": "2021-01-14T15:30:00Z"  
                },  
                "measuredValue": {  
                    "type": "Property",  
                    "value": "18.91",  
                    "unitCode": "MTR"  
                },  
                "thresholdType": {  
                    "type": "Property",  
                    "value": "LOWER"  
                },  
                "thresholdValue": {  
                    "type": "Property",  
                    "value": "20",  
                    "unitCode": "MTR"  
                }  
            }          
        },  
        {  
            "datasetId": "urn:ngsi-ld:Dataset:Breach2",  
            "value": {  
                "dateObserved": {  
                    "type": "Property",  
                    "value": "2021-01-14T15:45:00Z"  
                },  
                "measuredValue": {  
                    "type": "Property",  
                    "value": "18.91",  
                    "unitCode": "MTR"  
                },  
                "thresholdType": {  
                    "type": "Property",  
                    "value": "LOWER"  
                },  
                "thresholdValue": {  
                    "type": "Property",  
                    "value": "20",  
                    "unitCode": "MTR"  
                }  
            }          
        }  
    ],  
    "@context": [  
        "https://schema.lab.fiware.org/ld/context"  
    ]  
}  
```  
