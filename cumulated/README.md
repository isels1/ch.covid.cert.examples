# Cumulated mapping

The following chapters discribe the mapping of the cumulated arrays into the certificate content.

## Vaccines

The file "covid-19-vaccines.json" shall be used as whitelist for the valid vaccines.

| Cumulated JSON path | Certifivate JSON path |
| ------------------- | --------------------- |
| entries[n].prophylaxis_code | v[0].vp |
| entries[n].code | v[0].mp |
| entries[n].auth_holder_code | v[0].ma |

> Where "n" is the array pos of the corresponding vaccination entry.

## Tests

The file "covid-19-tests.json" shall be used as whitelist for the valid test kits.

| Cumulated JSON path | Certifivate JSON path |
| ------------------- | --------------------- |
| entries[n].type_code | t[0].tt |
| entries[n].manufacturer_code_eu | v[0].ma |

> Where "n" is the array pos of the corresponding test kit entry.
