# Propuesta TP DSW

## Grupo
### Integrantes
 52588 - Peppino, Valentin<br>
 52211 - Santinelli, Agustin<br>
 52425 - Zabaleta, Gianlucas<br>
 52398 - Ratti, Martin<br>

### Repositorios
* [Frontend](https://github.com/valenpeppi/FrontEnd-Venta-de-Entradas)
* [Backend](https://github.com/valenpeppi/BackEnd-Venta-de-Entradas)

## Tema
### Descripción
La plataforma consiste en un sistema de venta de entradas para eventos. Los organizadores pueden solicitar la creación de un evento, seleccionando un estadio
    previamente cargado en el sistema y completando los datos requeridos. Una vez enviada la solicitud, esta solicitud queda en estado pendiente y debe ser revisada y aprobada por un administrador.<br>
    
Cuando el evento es aprobado por el administrador, el evento quedará en estado pendiente para su publicación hasta que el organizador decida publicarlo. Una vez publicado en la plataforma, pasa a estar disponible para que los todos los usuarios puedan ver los eventos disponibles. Todos los eventos estarán organizados según su tipo, con el objetivo de facilitar la búsqueda. En caso de requerir información adicional sobre un evento, se proporcionará un detalle completo con todos los datos disponibles.<br>

En caso que un usuario se decida a realizar la compra de entradas para un determinado evento, deberá registrarse en la página si aun no lo ha hecho. A continuación, el proceso de selección variará según si el estadio cuenta con asientos numerados o no.<br>
   -Si el estadio es numerado, se mostrará primero la selección de sector y luego un mapa interactivo con los asientos disponibles dentro de ese sector.<br>
   -Si el estadio no es numerado, el usuario solo deberá elegir el sector deseado.<br>

Al momento de confirmar la compra, se solicitarán los datos necesarios y se procederá con el pago a través de los medios habilitados. Una vez finalizado el proceso, se mostrará al usuario un resumen detallado de su compra.

## Modelo    
<img width="1414" height="541" alt="image" src="https://github.com/user-attachments/assets/ca593d41-f697-424b-a6ce-7c69ff25840b" /><br>
(https://github.com/user-attachments/assets/20c47aa5-ba49-4d5c-ad4d-e2c1836824a5)<br>
Link de Draw.io: https://app.diagrams.net/#G1JQ4jZBuJwJ3PSq4Bxjy0-jp5qHoPxyZK#%7B%22pageId%22%3A%22C5RBs43oDa-KdzZeNtuy%22%7D


## Alcance Funcional 

### Alcance Mínimo


Regularidad:
|Req|Detalle|
|:-|:-|
|CRUD simple|1. CRUD TipoEvento<br>2. CRUD Usuario <br>3. CRUD Lugar|
|CRUD dependiente|1. CRUD Precio {depende de} Sector y Evento<br>2. CRUD Evento {depende de} Lugar y TipoEvento<br>3.CRUD Sector {depende de} CRUD Lugar|
|Listado<br>+<br>detalle| 1. Listado por nombre de evento, mostrando nombre, descripción, precio “desde” y fecha → detalle del evento muestra con estado, tipo, lugar, sectores disponibles, y si el evento/sector es enumerado o no enumerado.<br> 2. Listado por tipo de evento, muestra nombre de evento e imagen => detalle muestra nombre, descripción, precio “desde”, fecha, estado, tipo, lugar, sectores disponibles.|
|CUU/Epic|1. Comprar entradas para un evento publicado, contemplando flujo enumerado (selección de asientos en mapa dentro del sector) y flujo no enumerado (cantidad por sector).<br>2. Crear evento por organizador (queda pendiente), y publicar al ser aprobado por un administrador.|


Adicionales para Aprobación Directa
|Req|Detalle|
|:-|:-|
|CRUD |1. CRUD Usuario<br>2. CRUD Entrada<br>3. CRUD Evento<br>4. CRUD Sector<br>5. CRUD Venta<br>6. CRUD Precio<br>7. CRUD Lugar<br>8. CRUD TipoEvento<br>9. CRUD Butaca<br>10. CRUD LineaVenta|
|CUU/Epic|1. Comprar una entrada para un evento publicado<br>2. Crear un evento.<br>3. Aprobar/rechazar eventos pendientes.<br>4. Destacar eventos|


### Alcance Adicional Voluntario


|Req|Detalle|
|:-|:-|
|Listados |1. Eventos filtrados por descripcion parcial y tipo de evento. Muestra los datos del evento.|
|CUU/Epic|1. Asistente virtual de guiado.<br>2.  Ver historial de compras del usuario con tickets descargables.|
|Otros|1. Ayuda.<br>2. Preguntas frecuentes.<br>3. Sobre TicketApp.|

---

### Link a [PR](https://github.com/valenpeppi/tp/pulls)

