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
or

```

      -------------------------------------
      |                UI                  |
      -------------------------------------
 update  |  |                        | |
fitness  |  | Responce     Request   | |view 3D models
 param   |  |             with genes | |
    --------------   --------   -----------
    |   IGA      |---|  DB  |---|  Model  |
    | Controller |   | mysql|   | Creator |
    --------------   --------   -----------
         |                          
         | update genes             
         |                         
    ---------------------------------------
    |          Key / Value Store          |
    ---------------------------------------
```


## lock rule
When multiple users access to IGA controller simultaneously,  
exclusive control is needed with Genes.


