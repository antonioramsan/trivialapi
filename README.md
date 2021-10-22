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

### Resultado
```json
[
	{
		"modelname":"Expositor",
		"Expositor":1,
		"Nombre":"Antonio"
	}
]
```

### Recupera todos los registros:
> localhost:8081/api.viaken/x/Expositor

### Resultado
```json
[
	{
		"modelname":"Expositor",
		"Expositor":1,
		"Nombre":"Antonio"
	},
	{
		"modelname":"Expositor",
		"Expositor":2,
		"Nombre":"Leonardo"
	}	
]
```	
	
### Recupera todos los registros ordenados por nombre  descendente :
> localhost:8081/api.viaken/x/Expositor/Nombre_desc	

### Resultado
```json
[
	{
		"modelname":"Expositor",
		"Expositor":2,
		"Nombre":"Leonardo"
	},
	{
		"modelname":"Expositor",
		"Expositor":1,
		"Nombre":"Antonio"
	}	
]
```	


### Recupera todos los registros al nivel 2 :
> localhost:8081/api.viaken/x/Ciudad/L2	

### Resultado
```json
[
	{
		"modelname":"Ciudad",
		"Ciudad":1,
		"Nombre":"Monterrey",
		"Estado"{
			"modelname":"Estado",
			"Estado":1,
			"Nombre":"Nuevo León",
			"Pais":1
			}
	},
	{
		"modelname":"Ciudad",
		"Ciudad":2,
		"Nombre":"Tuxpam",
		"Estado"{
			"modelname":"Estado",
			"Estado":2,
			"Nombre":"Veracruz",
			"Pais":1
			}		
	}	
]
```	
	
> Estructura de la escritura

POST: SERVERNAME:PORT/api.NAME/ENV/ANYCOLLECTION/ACTIONAME

## Como Guardar


