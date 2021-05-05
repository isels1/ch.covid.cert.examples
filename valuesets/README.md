# Valuesets

The defined valuesets are based on the schema [valueset.json](https://github.com/eu-digital-green-certificates/ehn-dgc-schema/blob/main/valueset.json) published by the EU ([GitHub Repo](https://github.com/eu-digital-green-certificates/ehn-dgc-schema)).

## disease-agent-targeted

The disease-agent-targeted (key `tg` inside the `v`, `t` and `r` objects) is always the SNOMED CT code for COVID-19. The valueset can be found on the GitHub Repository of the `eu-digital-green-certificates` in the `ehn-dgc-schema` project under following [link](https://github.com/eu-digital-green-certificates/ehn-dgc-schema/blob/main/valuesets/disease-agent-targeted.json).

## vaccine-prophylaxis

The vaccination-prophylaxis (key `vp` inside the `v` object) is the SNOMED CT or ATC classification code for one of the covid-19 vaccine types. Following types are defined:

- `1119349007` --> SARS-CoV-2 mRNA vaccine (SNOMED CT)
- `1119305005` --> SARS-CoV-2 antigen vaccine (SNOMED CT)
- `J07BX03` --> covid-19 vaccines (ATC)

Use the ATC code, when the vaccine is neither an antigen nor a mRNA or the information is missing.
The valueset definition can be found on the GitHub Repository of the `eu-digital-green-certificates` in the `ehn-dgc-schema` project under following [link](https://github.com/eu-digital-green-certificates/ehn-dgc-schema/blob/main/valuesets/vaccine-prophylaxis.json).

The original valueset definition linked below contains a small incinsitency: The code `J07BX03` should be from ATC but is specified as a code from the SNOMED CT system. The correct valueset entry should be:

```json
"J07BX03": {
      "display": "covid-19 vaccines",
      "lang": "en",
      "active": true,
      "version": "2021-01",
      "system": "http://www.whocc.no/atc"
    }
```

## vaccine-medicinal-product

The vaccine-medicinal-product (key `mp` inside the `v` object) is the code of the Union Register of medicinal products or [Vaccine medicinal products not centrally authorized in the EU](https://webgate.ec.europa.eu/fpfis/wikis/x/ZYg-L).
