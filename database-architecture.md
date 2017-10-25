# Database Archtecture

We have two type of data.  

- Metadata -> MySQL
- GA (genes) -> Key/Value store

## Metadata

| Name | | |description|
|:-- |:--- |:--- |:--- |
| Group |       |            | One Group has One population(genes). |
|       | User  |            | Many Users (that are belonging to same Group) use one population symulataneously.|
|       |       | user-id    | |
|       |       | password   | |
|       |       | (tendency) | |

## GA (genes)

|key | value | 
|: ---|:---|
|Group| gene|

## Arch

```

      ----------------------------------
      |                UI               |
      ----------------------------------
 update  |                          |
fitness  |                          | view 3D models
 param   |                          |
    --------------   --------   -----------
    |   IGA      |---|  DB  |---|  Model  |
    | Controller |   | mysql|   | Creator |
    --------------   --------   -----------
         |                          |
         | update genes             | pic up
         |                          | some genes
    ---------------------------------------
    |          Key / Value Store          |
    ---------------------------------------
```

## lock rule
If 
We need block 
