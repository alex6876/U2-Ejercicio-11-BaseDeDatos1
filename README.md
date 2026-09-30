# Ejercicio — Base de Datos de Gestión de Venta de Entradas para Conciertos y Eventos



Proyecto enfocado en la modelación Entidad-Relación (DER / MER) e implementación de base de datos relacional para un sistema de boletaría y venta de entradas para conciertos, administrando recintos, sectores, eventos, clientes, transacciones de compra y tickets individuales emitidos.

---

## Descripción

El sistema modela una estructura de datos relacional para la venta comercialización e impresión de entradas a conciertos y espectáculos. Permite catalogar los recintos o estadios con sus respectivos sectores y capacidades de aforo, programar fechas de conciertos asociados a giras, registrar a los clientes usuarios, y procesar las órdenes de compra con la emisión individual de tickets por ubicación/sector.

---

## Funcionalidades e Implementación

### Entidades y Atributos

* Recinto:


* id_codigo-recinto: Clave primaria identificadora del lugar o estadio.


* nombre: Nombre del recinto (ej. estadio, teatro, anfiteatro).


* dirección: Domicilio o ubicación física del predio.


* ciudad: Ciudad donde se ubica el recinto.


* capacidad-maxima: Aforo total permitido en el recinto.




* Sector:


* id_sector: Clave primaria identificadora del sector o zona dentro del recinto.


* nombre: Denominación de la ubicación (ej. Platea Alta, Campo VIP, Tribuna).


* capacidad-maxima: Límite de capacidad propia de ese sector.


* precio base: Tarifa de referencia fijada para la ubicación.


* id_codigo-recinto: Clave foránea que lo relaciona con su recinto correspondiente.




* Concierto:


* id_concierto: Clave primaria identificadora del evento/concierto.


* titulo_gira: Nombre de la gira o título del show.


* fecha: Fecha en la que se realizará el concierto.


* hora: Horario de inicio del espectáculo.


* id_codigo-recinto: Clave foránea referenciando al recinto asignado.




* Cliente:


* id_dni: Clave primaria única identificadora del cliente comprador.


* nombre: Nombre del cliente.


* apellido: Apellido del cliente.


* correo electronico: Correo electrónico de contacto/acceso.


* contraseña: Clave de acceso a la cuenta de usuario.




* Compra:


* id_compra: Clave primaria única de la transacción comercial.


* fecha: Fecha en que se efectúa la compra.


* hora: Hora de la transacción.


* monto_total: Importe total facturado por la orden.


* id_dni: Clave foránea del cliente titular de la compra.




* Ticket:


* id_ticket: Clave primaria única del boleto/entrada emitido.


* id_dni: Clave foránea referenciando al comprador/poseedor.


* id_concierto: Clave foránea referenciando al evento reservado.


* id_sector: Clave foránea referenciando a la zona/sector asignado.


* id_compra: Clave foránea referenciando a la orden de compra que originó el ticket.





---

## Relaciones del Modelo

1. Recinto ↔ Sector (Relación 1:N):


* Un recinto posee múltiples sectores o ubicaciones diferenciadas, pero cada sector forma parte de un único recinto.




2. Recinto ↔ Concierto (Relación 1:N):


* Un recinto puede albergar múltiples conciertos a lo largo del tiempo, pero cada concierto tiene lugar en un recinto asignado.




3. Sector ↔ Concierto (Relación 1:N / N:M implicita):


* Los sectores de un recinto están habilitados para la disponibilidad de ubicaciones en los conciertos realizados en él.




4. Cliente ↔ Compra (Relación 1:N):


* Un cliente puede realizar múltiples transacciones o compras de boletos, pero cada orden corresponde a un único cliente.




5. Compra ↔ Ticket (Relación 1:N):


* Una orden de compra agrupa uno o más tickets/entradas adquiridos en la misma transacción.




6. Cliente ↔ Ticket (Relación 1:N):


* Un cliente puede estar asociado a múltiples boletos individuales emitidos a su nombre.




7. Concierto ↔ Ticket (Relación 1:N):


* Un concierto registra la emisión de múltiples tickets vendidos para las distintas localidades.




8. Sector ↔ Ticket (Relación 1:N):


* Un sector particular incluye la emisión de múltiples tickets pertenecientes a su zona de aforo.
