# ch.covid.cert.examples

Examples for the codiv-19-certificat

*Please note that the schema files can be invalid or outdated due to the work in progress of the project.*

*Look up the newest Schema Version online, published by the EU. The example .json files are based on the Document `Guidelines on Value Sets for Digital Green Certificates Version 1.0 2021-04-21` [Link](https://ec.europa.eu/health/sites/health/files/ehealth/docs/digital-green-certificates_dt-specifications_en.pdf)*

## General

There is a general part, all cert types must include.

```json
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
    // String, maxLength: 16 according dsc in "DGC.Types.schema.json"
    "dsc": "doc-sign-certifi",
    // Next elements would be the type spesific. Definition in separat chapters.
    ...
}

```

Followed by one of the elements `v`, `t` or `r`.

## Vaccination

## Tested

## Recovery
