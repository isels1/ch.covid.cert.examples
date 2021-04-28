# ch.covid.cert.examples

Examples for the codiv-19-certificat

*Please note that the schema files can be invalid or outdated due to the work in progress of the project.*

*Look up the newest Schema Version online, published by the EU. The example .json files are based on the Document `Guidelines on Value Sets for Digital Green Certificates Version 1.0 2021-04-21` [Link](https://ec.europa.eu/health/sites/health/files/ehealth/docs/digital-green-certificates_dt-specifications_en.pdf)*

## General

There is a general part, all cert types must include.

```javascript
{
    // Surname(s), forename(s) - in that order 
    // Array of objects, defined in "DGC.schema.json"
    "nam": [
        // Object person_name as defined in "DGC.Core.Types.schema.json"
        {
            "_fn": "Červenková Panklová",
            "_gn": "Jiřina Alena"
        }
    ],
    // Date of Birth, ISO 8601
    // String with given pattern according dob_valid_date_range in "DGC.Core.Types.schema.json"
    "dob": "1987-03-22",
    // Document Signing Certificate: 8 bytes
    // First 8 bytes of the SHA-256 fingerprint
    // String, maxLength: 16 according dsc in "DGC.Types.schema.json"
    "dsc": "doc-sign-certifi",
    // Next elements would be the type spesific. Definition in separat chapters.
    ...
}

```

Followed by one of the elements `v`, `t` or `r`.

## Vaccination

The vaccination part is defined as followed:

```javascript
{
    // Previous elements aare the generic ones. Definition above.
    ...
    // Vaccination group
    // Array of objects, defined in "DGC.schema.json"
    "v": [
        // Object vaccination_entry as defined in "DGC.Types.schema.json"
        {
            // disease or agent targeted
            // Value Sets for Digital Green Certificates. version 1.0, 2021-04-16, section 2.1
            // Type object, required code & system according disease-agent-targeted in "DGC.ValueSets.schema.json"
            "tg": {
                "code": "840539006",
                "system": "2.16.840.1.113883.6.96"
            },
            // vaccine or prophylaxis
            // Value Sets for Digital Green Certificates. version 1.0, 2021-04-16, section 2.2
            // Type object, required code with oneOf definition according vaccine-prophylaxis in "DGC.ValueSets.schema.json"
            "vp": {
                "code": "1119349007"
            },
            // vaccine medicinal product
            // Value Sets for Digital Green Certificates. version 1.0, 2021-04-16, section 2.3
            // Type object, required code with oneOf definition according vaccine-medicinal-product in "DGC.ValueSets.schema.json"
            // Open: Definition of CH-specific product-codes?
            "mp": {
                "code": "EU/1/20/1507"
            },
            // Marketing Authorization Holder - if no MAH present, thenmanufacturer
            // Value Sets for Digital Green Certificates. version 1.0, 2021-04-16, section 2.3
            // Type object, required code with oneOf definition according vaccine-mah-manf in "DGC.ValueSets.schema.json"
            // Open: Definition of CH-specific organisation identifier?
            "ma": {
                "code": "ORG-100030215" 
            },
            // Dose number
            // Int min 1, max 9 according dose_posint in "DGC.Core.Types.schema.json"
            "dn": 1,
            // Total Series of Doses
            // Int min 1, max 9 according dose_posint in "DGC.Core.Types.schema.json"
            "sd": 2,
            // Date of Vaccination, ISO 8601
            // String containing date according dt in "DGC.Types.schema.json"
            "dt": "2021-04-22",
            // Country of Vaccination, ISO 3166 (where possible)
            // String with pattern [A-Z]{1,10} according country_vt in "DGC.Core.Types.schema.json"
            "co": "CH",
            // Certificat Issuer
            // String with max length 50 according issuer in "DGC.Core.Types.schema.json"
            // In CH the value shall be fixed to BAG/OFSP/FOPH --> no not forget the translations/languages (EN/DE/FR/IT)
            "is": "Bundesamt für Gesundheit (BAG)",
            // Unique Certificate Identifier: UVCI
            // Unique string maxLength 50 according certification_id in "DGC.Core.Types.schema.json"
            // Example according definition in https://ec.europa.eu/health/sites/health/files/ehealth/docs/vaccination-proof_interoperability-guidelines_en.pdf ANNEX 2
            "ci": "1.0.0:CH:5fhLA2gdjkk21123AABB123:12"
        }
    ],
}

```

## Tested

## Recovery
