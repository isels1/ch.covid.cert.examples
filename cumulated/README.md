# Cumulated

The following chapters discribe the mapping of the cumulated arrays into the certificate content.

## Mapping

### Vaccines

The file "covid-19-vaccines.json" shall be used as whitelist for the valid vaccines.

| Cumulated JSON path | Certificate JSON path |
| ------------------- | --------------------- |
| entries[n].prophylaxis_code | v[0].vp |
| entries[n].code | v[0].mp |
| entries[n].auth_holder_code | v[0].ma |

> Where "n" is the array pos of the corresponding vaccination entry.

### Tests

The file "covid-19-tests.json" shall be used as whitelist for the valid test kits.

| Cumulated JSON path | Certificate JSON path |
| ------------------- | --------------------- |
| entries[n].type_code | t[0].tt |
| entries[n].manufacturer_code_eu | v[0].ma |

> Where "n" is the array pos of the corresponding test kit entry.

## Structure

Following two chapters shortly describe the structures of the whitelist files.

### Vaccines structure

The structure of the "covid-19-vaccines.json":

```javascript
{
    // Id of the list
    "Id": "Covid 19 Vaccines",
    // Last modified date
    "Date": "2021-05-05",
    // Version code
    "Version": "1.0.0",
    // Entries array, where all acceppted vaccines are listed
    "entries": [
        // Object containing merged information of a vaccine
        {
            // Name of vaccination as string
            // Current source: "display" value of ../valuesets/vaccine-medical-product.json "valueSetValues" entries.
            "name": "Comirnaty",
            // Code of vaccination as string
            // Current source: key of ../valuesets/vaccine-medical-product.json "valueSetValues" entries.
            "code":"EU/1/20/1528",
            // Name of prophylaxos type as string
            // Current source: "display" value of ../valuesets/vaccine-prophylaxis.json "valueSetValues" entries.
            "prophylaxis": "COVID-19 mRNA vaccine",
            // Code of prophylaxos type as string
            // Current source: key of ../valuesets/vaccine-prophylaxis.json "valueSetValues" entries.
            "prophylaxis_code": "1119349007",
            // Name of authorization holder as string
            // Current source: "display" value of ../valuesets/vaccines-auth-holders.json "valueSetValues" entries.
            "auth_holder": "BioNTech Manufacturing GmbH",
            // Code of authorization holder as string
            // Current source: key of ../valuesets/vaccines-auth-holders.json "valueSetValues" entries.
            "auth_holder_code": "ORG-100030215",
            // If authorization is active
            // Current source: "active" value of ../valuesets/vaccine-medical-product.json "valueSetValues" entries.
            "active": "true"
        }
    ]
}

```

#### Maintenance

Following table shows the mapping from the value sets to the cumulated files:
| Cumulated JSON path | vaccine-medical-product.json | vaccine-prophylaxis.json | vaccines-auth-holders.json |
| ------------------- | ---------------------------- | ------------------------ | -------------------------- |
| entries[n].name | valueSetValues.x<sup>1</sup>.display | - | - |
| entries[n].code | valueSetValues.x<sup>1</sup> | - | - |
| entries[n].prophylaxis | - | valueSetValues.y<sup>2</sup>.display | - |
| entries[n].prophylaxis_code | - | valueSetValues.y<sup>2</sup> | - |
| entries[n].auth_holder | - | - | valueSetValues.z<sup>3</sup>.display |
| entries[n].auth_holder_code | - | - | valueSetValues.z<sup>3</sup> |
| entries[n].active | valueSetValues.x<sup>1</sup>.active | - | - |

> <sup>1</sup>: x represents the key names (medical product number) of the objects in the valueSetValues object.
> <sup>2</sup>: y represents the key names (SNOMED CT or ATC code) of the objects in the valueSetValues object.
> <sup>3</sup>: z represents the key names (organisation id) of the objects in the valueSetValues object.

### Tests structure
