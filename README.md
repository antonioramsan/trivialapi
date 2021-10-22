# Trivial API
> Antonio Ramírez Santander



## Como Leer

Nota:Solo se usan los Verbos GET y POST

> Estructura de la lectura.

```plain
GET: SERVERNAME:PORT/api.NAME/ENV/MODELNAME/ID/SORTFIELD1_[desc|asc],SORTFIELD2_[desc|asc]/L[INSTANCELEVEL]/_DTONAME/{"FILTERPROPERTY1":VALUE1}/P1X10
```

## Ejemplos:
### Recupera 1 registro:
> localhost:8081/api.viaken/x/Expositor/1   o  localhost:8081/api.viaken/x/Expositor/{"Expositor":1}  

### Recupera todos los registros:
> localhost:8081/api.viaken/x/Expositor
	
### Recupera todos los registros ordenados por nombre  descendente :
> localhost:8081/api.viaken/x/Expositor/Nombre_desc	

### Recupera todos los registros al nivel 2 :
> localhost:8081/api.viaken/x/Estado/L2	
	
> Estructura de la escritura

POST: SERVERNAME:PORT/api.NAME/ENV/ANYCOLLECTION/ACTIONAME

## Como Guardar


