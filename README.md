# jsontodw 🔄

![PowerBuilder](https://img.shields.io/badge/PowerBuilder-2025-005C84?style=flat-square&logo=sap&logoColor=white)
![JSON](https://img.shields.io/badge/JSON-import-000000?style=flat-square&logo=json&logoColor=white)
![DataStore](https://img.shields.io/badge/DataStore-din%C3%A1mico-1F6FEB?style=flat-square)
![Blog](https://img.shields.io/badge/blog-rsrsystem-FF5722?style=flat-square&logo=blogger&logoColor=white)

## 📋 ¿Qué es esto?

Seguro que os ha pasado: llega un **JSON de una API** que no controláis, queréis volcarlo a un DataWindow…
pero **no sabéis la estructura de antemano** y, además, cada elemento del array puede traer más o menos campos.
Un lío para montar el DataWindow "a mano".

Este ejemplo demuestra cómo **convertir un JSON a un DataStore sin usar el objeto Transaction y sin conocer
de antemano la estructura del JSON**. La app inspecciona el JSON, deduce las columnas sobre la marcha y te
deja los datos en un DataStore listo para usar.

## ✨ Cómo funciona

El truco está en aceptar una premisa razonable y trabajar a partir de ahí:

- El JSON de entrada es un **array de objetos JSON**.
- Cada objeto puede tener **más o menos campos** que los demás (no pasa nada).
- Si un campo es a su vez un **array u otro JSON anidado**, no lo intentamos explotar en columnas: lo
  guardamos **como string** en su columna. Así nada se rompe y no pierdes la información.

Con eso, el ejemplo:

1. Recorre el array y descubre el **conjunto de campos** que aparecen.
2. Construye dinámicamente un **DataStore** con esas columnas.
3. Vuelca cada elemento, metiendo los anidados como texto.

Los objetos clave que tenéis dentro:

| Objeto            | Para qué sirve                                               |
|-------------------|-------------------------------------------------------------|
| `u_datastore.sru` | DataStore extendido que recibe el JSON y se autoconfigura.  |
| `u_datawindow.sru`| Variante para DataWindow visual.                            |
| `gf_endpoint.srf` | Ayuda para traer el JSON desde un endpoint.                 |
| `w_main.srw`      | La ventana de demostración.                                  |

Todo **sin tocar el objeto Transaction**: aquí no hay tabla ni base de datos detrás, solo el JSON y un
DataStore en memoria.

## 🛠️ Requisitos

- **PowerBuilder 2025** para abrir la solución y compilar.
- Nada más: el ejemplo no necesita base de datos.

## ▶️ Cómo probarlo

1. Clona el repo (viene **en modo solución**).
2. Abre `jsontodw.pbsln` en el IDE de PowerBuilder.
3. Ejecuta `w_main`, dale un JSON (array de objetos) y mira cómo aparece volcado en el DataStore.

> ¿Solo quieres verlo? Tenéis el `jsondw.exe` ya compilado en la carpeta.

## 🔗 Repo PowerBuilder

Ejemplo publicado **en modo solución**:
<https://github.com/rasanfe/jsontodw>

---

> ¡Nos vemos en el próximo artículo! Y recuerda: en PowerBuilder, los límites solo están en nuestra imaginación. 🚀

📨 **Blog:** <https://rsrsystem.blogspot.com/>
