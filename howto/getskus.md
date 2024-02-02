#Get available SKUs for MySQL/Postgres single server


## Azure Database for MySQL single server

```shell
az mysql server list-skus -l westeurope --query "[].{id:id, maxStorageMb:maxStorageMb, minStorageMb:minStorageMb,  sku:serviceLevelObjectives[].id}"
```

```shell
az mysql server list-skus -l westeurope --query "[].{id:id, maxStorageMb:maxStorageMb, minStorageMb:minStorageMb,  sku:serviceLevelObjectives[].id}"
```


## Azure Database for PostgreSQL Single Server 

```shell
az postgres server list-skus -l westeurope --query "[].{id:id, maxStorageMb:maxStorageMb, minStorageMb:minStorageMb,  sku:serviceLevelObjectives[].id}"
```

```shell
az postgres server list-skus -l westeurope --query "[].{id:id, maxStorageMb:maxStorageMb, minStorageMb:minStorageMb,  sku:serviceLevelObjectives[].id}"
```

Flexible server
For prices please refer to https://aka.ms/postgres-pricing

 
## Postgres single and flexible server kql:

```kql
resources
| where type in (
    "microsoft.dbforpostgresql/servers",
    "microsoft.dbforpostgresql/flexibleservers") 
| project name, ['type'], location, sku.name
| sort by (tolower(tostring(name))) asc
```