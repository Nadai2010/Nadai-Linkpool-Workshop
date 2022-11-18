# NadaiFlight External Adapter Chainlink 

Esta repo es una guia del tutorial de Chainlink sobre `External Adapters` para la comunidad hispano hablante. Esta demostración muestra cómo construir un external adapter que se conecta a un nodo Oracle de Chainlink para que sus contratos inteligentes puedan obtener datos arbitrarios de una API externa. 

En este caso veremos como un vuelo con 300 pasajeros deja una mancha en el ozono. Verificaremos por oráculos de Chainlink y escribiremos en la Blockchain cuanto ha sido su consumo llamando a la Api, siendo estos datos de unas carateristicas inmutables ` por naturaleza de la BLock`, pudiendo verificar siempre su estado inaltereable y con él, los cambios de emisiones de `CO2` por vuelo. 

### Hipotético casos de uso

Las regulaciones han puesto pie en el asunto. A partir del próximo mes los gastos de CO2 serán gestionados por Smart contract en la Blockchain, las compañias depositarán unos Fondos de Garantias para cubrir legislación. Dependiendo de la emisión final podremos optar a:

* CO2 % Encima de normativa = Sanción de X usdt, autopagable de Fondos Garatía CO2 en la medición final del mes.

* CO2 % Medio de normativa = Sin sanción ni bonificación, autopagable de Fondos Garatía CO2 en la medición final del mes.

* CO2 % Bajo de normativa = Bonificación de X usdt, autopagable de Fondos Garatía CO2 en la medición final del mes.

Como vemos este simple caso de uso haria que esta tecnología sea inmutable, trasnparente y auditable por cualquiera.

### Documentos externos oficiales

Aquí estarán todos los enlaces oficiales, herramientas y documentos usados para este Workshop.

* [Workshop External Adapters 📹](https://www.youtube.com/watch?v=fs3Xg3fZ2Sg)
* [Gilbert Oficial](https://github.com/teterabOb/cl-ea-linkpool-workshop) Repositorio Github oficial del Workshop
* [External Adapters](https://docs.chain.link/docs/external-adapters/) 
* [Chainlink NodeJS External Adapter](https://github.com/thodges-gh/CL-EA-NodeJS-Template.git)Está basado en este Template.La plantilla proporciona un marco básico para desarrollar adaptadores externos de Chainlink en NodeJS.
* [Api Climatiq](https://www.climatiq.io/). Utilice su API REST distribuida globalmente con aplicaciones que se ejecutan en cualquier dispositivo o servidor ubicado en cualquier centro de datos. Integre inteligencia de emisiones de carbono en sus aplicaciones.
* [Climatiq Doc](https://www.climatiq.io/docs)
* [Sección de Vuelos](https://www.climatiq.io/docs#travel-flights) Además del cálculo directo de las emisiones por pasajero-kilómetro, pasajero-milla, tonelada-kilómetro o tonelada-milla, Climatiq pone a disposición puntos finales para calcular las emisiones en función de los aeropuertos de salida y llegada. La API seleccionará automáticamente un factor de emisión, actualmente basado en la elección del valor de CO2e más alto disponible.


## Crear su propio adaptador a partir de esta plantilla

Primero clonaremos este repositorio y cambiar `ExternalAdapterProject` abajo al nombre de su proyecto, en este caso por `NadaiExternalAdapterProject`

```bash
git clone https://github.com/thodges-gh/CL-EA-NodeJS-Template.git ExternalAdapterProject
```

Imagen

Entra al nuevo directorio creado

```bash
cd ExternalAdapterProject
```

Puedes remover el historial repositorio de git ejecutando:

```bash
rm -rf .git
```

## Instalar localmente

Instalar dependencias:

```bash
yarn
```

imagen

### Run

Correr la aplicación de manera local (por defecto en el peurto 8080)

```bash
yarn start
```

**NOTA: Una vez se ejecute el nodo, no cerrar TERMINAL, abrir una nueva para continuar pruebas**
Imagen

## DigitalOcean

DigitalOcean tiene los servicios de computación en la nube que necesita, con precios predecibles, documentación sólida y escalabilidad para respaldar su crecimiento en cualquier etapa. Iremos a [DigitalOcean](https://www.digitalocean.com/) para hacer nuestro registro, en nuestro caso conectamos con Github y luego procedimos a la verficación. 

Aqui deberemos de `Verificar su identidad` y de pagar `5 USD` con un método de verificación centralizada, en este caso usamos `Paypal`. Una vez verficado y realizados estos pasos podremos seguir, desbloqueando el menu principal.

imagen

En digital iremos a `Create` y escogeremos `Apps`. Dentro podremos configurar con un par de click, que repo escoger sin tener que definir mas valores manuales, para ello ajustaremos `Manage account` y daremos permisos desde `Github`.

imagen

**NOTA: Para ver el repositorio actual, cargue previamente su contenido mediante un Fork o Manual de este repositorio**

## Llamar al external adapter/API Server

Localhost

```bash
curl -X POST -H "content-type:application/json" "http://localhost:8080" --data '{"id": 1, "data": {"from": "ONT", "to": "SCL","passengers": 300,"class": "unknown" } }'
```
## Llamar al external adapter/API Server

URL Pública

[API_Endpoint] = https://orca-app-wt4ks.ondigitalocean.app/

```bash
curl -X POST -H "content-type:application/json" "API_ENDPOINT" --data '{"id": 1, "data": {"from": "ONT", "to": "SCL","passengers": 300,"classFlight": "unknown" } }'
```

```bash
curl -X POST -H "content-type:application/json" "https://orca-app-wt4ks.ondigitalocean.app/" --data '{"id": 1, "data": {"from": "ONT", "to": "SCL","passengers": 300,"classFlight": "unknown" } }'
```


## Arquitectura

![alt Dibujo de arquitectura mostrando la interacción dentro del sistema](./img/ea-arquitectura.jpg "Diagrama de Arquitectura")

