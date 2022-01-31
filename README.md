# Trivial API
> Antonio Ramírez Santander

## Como obtener un token para el usuario 
curl -u zaprax:testpass http://trivialsoft.com/api.viakon/x/token -d "grant_type=password&username=USER&password=PWD"

## Como Leer

Nota:Solo se usan los Verbos GET y POST

> Estructura de la lectura.

```plain
GET: SERVERNAME:PORT/api.NAME/ENV/MODELNAME/ID/SORTFIELD1_[desc|asc],SORTFIELD2_[desc|asc]/L[INSTANCELEVEL]/_DTONAME/{"FILTERPROPERTY1":VALUE1}/P1X10
```

## Ejemplos:
### Recupera 1 registro:
> localhost:8081/api.viaken/x/Expositor/1   
> localhost:8081/api.viaken/x/Expositor/{"Expositor":1}  

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


## Ejemplo de Encuesta

> Caso Hipotetico "Los colores de una camisa solo estan disponibles para la Talla Grande"

* Nota 1: En la respuesta "Talla G" de la Pregunta 1 existe una lista llamada "Dependientes" que lista los id de la Preguntas que dependen de esta
* Nota 2: Además en la Pregunta 2 existe una propiedad llamanda "DependeDe" que contiene la referencia a la Respuesta de la cual depende

```json
[
    {
        "modelname": "Encuesta",
        "Encuesta": "1",
        "Evento": "1",
        "Nombre": "Encuesta 1",
        "Preguntas": [
            {
                "modelname": "PreguntaEncuesta",
                "PreguntaEncuesta": "1",
                "Encuesta": "1",
                "TipoPregunta": "1",
                "Texto": "Cual es su talla de Camisa?",
                "Respuestas": [
                    {
                        "modelname": "RespuestaEncuesta",
                        "RespuestaEncuesta": "1",
                        "PreguntaEncuesta": "1",
                        "Nombre": "Talla M",
                        "Dependientes": []
                    },
                    {
                        "modelname": "RespuestaEncuesta",
                        "RespuestaEncuesta": "2",
                        "PreguntaEncuesta": "1",
                        "Nombre": "Talla G",
                        "Dependientes": [
                            {
                                "PreguntaEncuesta": "2"
                            }
                        ]
                    },
                    {
                        "modelname": "RespuestaEncuesta",
                        "RespuestaEncuesta": "3",
                        "PreguntaEncuesta": "1",
                        "Nombre": "Talla XL",
                        "Dependientes": []
                    }
                ],
                "DependeDe": []
            },
            {
                "modelname": "PreguntaEncuesta",
                "PreguntaEncuesta": "2",
                "Encuesta": "1",
                "TipoPregunta": "1",
                "Texto": "Cual es el Color de Su Camisa?",
                "Respuestas": [
                    {
                        "modelname": "RespuestaEncuesta",
                        "RespuestaEncuesta": "4",
                        "PreguntaEncuesta": "2",
                        "Nombre": "Azul",
                        "Dependientes": []
                    },
                    {
                        "modelname": "RespuestaEncuesta",
                        "RespuestaEncuesta": "5",
                        "PreguntaEncuesta": "2",
                        "Nombre": "Negra",
                        "Dependientes": []
                    },
                    {
                        "modelname": "RespuestaEncuesta",
                        "RespuestaEncuesta": "6",
                        "PreguntaEncuesta": "2",
                        "Nombre": "Blanca",
                        "Dependientes": []
                    }
                ],
                "DependeDe": [
                    {
                        "RespuestaEncuesta": {
                            "modelname": "RespuestaEncuesta",
                            "RespuestaEncuesta": "2",
                            "PreguntaEncuesta": "1",
                            "Nombre": "Talla G",
                            "Dependientes": [
                                {
                                    "PreguntaEncuesta": "2"
                                }
                            ]
                        }
                    }
                ]
            }
        ]
    },
    {
        "modelname": "Encuesta",
        "Encuesta": "3",
        "Evento": "1",
        "Nombre": "Encuesta 2",
        "Preguntas": []
    }
]
```

> Estructura de la escritura

POST: SERVERNAME:PORT/api.NAME/ENV/ANYCOLLECTION/ACTIONAME

## Como Guardar
```plain
[
{
"modelname":"Encuesta",
"Encuesta":3,
"Nombre":"Encuesta DOS"
}
]
```

> Ejemplo de recuperacion

## Recuperar Encuesta 1
```plain
http://trivialsoft.com/api.viakon/x/Encuesta/1/_full 
```


## Recuperar una imagen

```plain
//  esta es la estructura de un instancia de Archivo(Imagen)
// Contenido no viene lleno por default
{
        "modelname": "Archivo",
        "Archivo": "13",
        "Nombre": "test",
        "NombreOriginal": "test.png",
        "Descripcion": "",
        "MimeType": "image\/png",
        "PathSistema": "66f3ffcee7c00ab2f1272a12c00f9846.png",
        "TipoArchivo": "1",
        "Contenido": ""
}

// -- para recuperar la instancia con el contenido en Base64 usar el siguiente EndPoint
http://trivialsoft.com/api.viakon/x/Archivo.ArchivoApp/Read/{"id":"66f3ffcee7c00ab2f1272a12c00f9846.png"}

```

## Recuperar los tipos de preguntas 

```plain
http://trivialsoft.com/api.viakon/x/TipoPregunta
```

## Ejemplo de guardar respuestas del usuario 
> POST: http://trivialsoft.com/api.viakon/x/anycollection

```plain
[
{
	"modelname":"RespuestaUsuario",
	"RespuestaUsuario":"",
	"Encuesta":1,
	"Usuario":1,
	"PreguntaEncuesta":33,
	"Valor":"Antonio"
}
,
{
	"modelname":"RespuestaUsuario",
	"RespuestaUsuario":"",
	"Encuesta":1,
	"Usuario":1,
	"PreguntaEncuesta":35,
	"Valor":"Ramirez"
}
,
{
	"modelname":"RespuestaUsuario",
	"RespuestaUsuario":"",
	"Encuesta":1,
	"Usuario":1,
	"PreguntaEncuesta":36,
	"Valor":"Santander"
}
,
{
	"modelname":"RespuestaUsuario",
	"RespuestaUsuario":"",
	"Encuesta":1,
	"Usuario":1,
	"PreguntaEncuesta":37,
	"Valor":"02/02/1981"
},
{
	"modelname":"RespuestaUsuario",
	"RespuestaUsuario":"",
	"Encuesta":1,
	"Usuario":1,
	"PreguntaEncuesta":38,
	"Valor":"Diana Martinez"
},
{
	"modelname":"RespuestaUsuario",
	"RespuestaUsuario":"",
	"Encuesta":1,
	"Usuario":1,
	"PreguntaEncuesta":39,
	"RespuestaEncuesta":13,
	"Valor":""
}
]
```

## Respuesta Satisfactoria

```json
{
    "resp": "Actualizado",
    "id": "263",
    "model": "RespuestaUsuario",
    "status": 1,
    "updates": "{'RespuestaUsuario_257':'','RespuestaUsuario_258':'','RespuestaUsuario_259':'','RespuestaUsuario_260':'','RespuestaUsuario_261':'','RespuestaUsuario_262':'','RespuestaUsuario_263':''}",
    "exmessage": "",
    "validations": []
}

```

## Respuesta No Satisfactoria
```json
{
    "status": 0,
    "exmessage": "",
    "updates": "{}",
    "resp": "",
    "model": "",
    "validations": [
		{
		  "errcode": "0001",
		  "desc":"Se acabaron los lugares del Horario",
		  "id": 50 
		}
	]
}
```

## Consultar si ta contesto 

GET: http://localhost:81/api.viakon/x/RespuestaUsuario

> Si el responde un array de longitud 0 no ha contestado

> Nota: ***Solo el admin puede recuperar todas las respuestas***

## Ejemplo de respuesta:
```json
[
    {
        "modelname": "RespuestaUsuario",
        "RespuestaUsuario": "566",
        "Encuesta": "1",
        "Usuario": null,
        "PreguntaEncuesta": "33",
        "RespuestaEncuesta": null,
        "Valor": "Leonardo"
    },
    {
        "modelname": "RespuestaUsuario",
        "RespuestaUsuario": "567",
        "Encuesta": "1",
        "Usuario": null,
        "PreguntaEncuesta": "35",
        "RespuestaEncuesta": null,
        "Valor": "Santos"
    },
    {
        "modelname": "RespuestaUsuario",
        "RespuestaUsuario": "568",
        "Encuesta": "1",
        "Usuario": null,
        "PreguntaEncuesta": "36",
        "RespuestaEncuesta": null,
        "Valor": ""
    },
    {
        "modelname": "RespuestaUsuario",
        "RespuestaUsuario": "569",
        "Encuesta": "1",
        "Usuario": null,
        "PreguntaEncuesta": "37",
        "RespuestaEncuesta": null,
        "Valor": "02/02/1985"
    },
    {
        "modelname": "RespuestaUsuario",
        "RespuestaUsuario": "570",
        "Encuesta": "1",
        "Usuario": null,
        "PreguntaEncuesta": "38",
        "RespuestaEncuesta": null,
        "Valor": "Uno Dos Tres"
    },
    {
        "modelname": "RespuestaUsuario",
        "RespuestaUsuario": "571",
        "Encuesta": "1",
        "Usuario": null,
        "PreguntaEncuesta": "39",
        "RespuestaEncuesta": "13",
        "Valor": ""
    },
    {
        "modelname": "RespuestaUsuario",
        "RespuestaUsuario": "572",
        "Encuesta": "1",
        "Usuario": null,
        "PreguntaEncuesta": "67",
        "RespuestaEncuesta": "48",
        "Valor": ""
    }
]
```








