# Cumulated mapping

The following chapters discribe the mapping of the cumulated arrays into the certificate content.

## vaccines

The file "covid-19-vaccines.json" shall be used as whitelist for the valid vaccines.

| Cumulated JSON path | Certifivate JSON path |
| ------------------- | --------------------- |
| entries[n].prophylaxis_code | v[0].vp |

> Where "n" is the array pos of the corresponding vaccination entry.
