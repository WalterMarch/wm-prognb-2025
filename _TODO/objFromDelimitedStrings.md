# Object from delimited strings

Given a delimited string of column names `"name|abbreviation|capital"` and an array of data strings

```json
[
    "Alabama|AL|Montgomery",
    "Alaska|AK|Juneau",
    "Arizona|AZ|Phoenix",
    "Arkansas|AR|Little Rock"
]
```

construct an array of objects

```json
[
    {
        "name": "Alabama",
        "abbreviation": "AL",
        "capital": "Montgomery"
    },
    {
        "name": "Alaska",
        "abbreviation": "AK",
        "capital": "Juneau"
    },
    {
        "name": "Arizona",
        "abbreviation": "AZ",
        "capital": "Phoenix"
    },
    {
        "name": "Arkansas",
        "abbreviation": "AR",
        "capital": "Little Rock"
    }
]
```
