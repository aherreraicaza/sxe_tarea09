# Tarea 09: Odoo

## Arranque

Arranco Docker desde la terminal de IntelliJ usando Ubuntu en WSL:

"wsl -d Ubuntu -u root --cd $PWD -- docker compose up -d"

Odoo está en http://localhost:8069 y pgAdmin en http://localhost:5050. Para pgAdmin uso el correo y la contraseña del .env. No subo .env ni config/odoo.local.conf a GitHub.

Para instalarlo en otro equipo, copio .env.example a .env y completo los datos. También copio config/odoo.conf a config/odoo.local.conf y añado allí una línea "admin_passwd =" con mi contraseña maestra.

## Bases de datos

Creé demo con datos de ejemplo y primo vacía. En las dos puse español y España. La guía también llama real a la base vacía, pero al final pide primo.

![Gestor con demo y primo](capturas/bases.png)

## Productos

Miré un ejemplo de cada tipo. En la silla los impuestos estaban vacíos; la protección de suelo tenía IVA del 21% en venta y compra. El servicio no tenía impuestos y el set era una combinación de productos.

![Bien con inventario](capturas/producto-stock.png)

![Bien sin inventario](capturas/producto-sin-stock.png)

![Servicio](capturas/producto-servicio.png)

![Combinación](capturas/producto-combinacion.png)

## Venta y factura

Abrí una empresa y una persona vinculada. Luego hice un cliente de prueba con CIF, dirección de Vigo y etiqueta. Los datos son inventados.

![Empresa](capturas/contacto-empresa.png)

![Persona vinculada](capturas/contacto-persona.png)

![Cliente nuevo](capturas/cliente.png)

Creé Hora de soporte por 40 € con IVA del 21% y Libro técnico por 25 € con IVA del 4%. Puse uno de cada en el presupuesto S00025, lo envié a una dirección de prueba y lo confirmé.

![Presupuesto](capturas/presupuesto.png)

![Pedido confirmado con el envío del presupuesto en el historial](capturas/presupuesto-enviar.png)

![Pedido confirmado](capturas/pedido.png)

La factura suma 65 € de base y 9,40 € de IVA: 74,40 € en total. La confirmé y registré un pago de prueba. Quedó como Pagado.

![Factura con los IVA](capturas/factura-iva.png)

![Factura pagada](capturas/pagada.png)

El PDF está en [factura.pdf](capturas/factura.pdf). También programé una llamada para el cliente.

![Llamada](capturas/llamada.png)

## Búsqueda y modo desarrollador

En Facturación filtré las facturas registradas, agrupé por socio y guardé el favorito Publicadas por cliente.

![Búsqueda guardada](capturas/favorito.png)

La factura de proveedor que abrí era de Gemini Furniture.

![Factura de proveedor](capturas/proveedor.png)

Activé el modo desarrollador desde Ajustes y probé también la dirección "?debug=1". Los campos del contacto son email y vat, del modelo res.partner. La factura usa el modelo account.move.

![Activación desde Ajustes](capturas/debug-ajustes.png)

![Odoo con modo desarrollador](capturas/debug-url.png)

![Campo vat](capturas/campo-vat.png)

![Campo email](capturas/campo-email.png)

![Modelo de factura](capturas/modelo-factura.png)

## Incidencias

| Fecha | Síntoma | Causa | Solución |
| --- | --- | --- | --- |
| 14/11/2026 | Odoo no arrancaba: "no such option: --admin-passwd". | Odoo 19 no acepta esa opción. | Puse la contraseña maestra en config/odoo.local.conf. |
| 15/11/2026 | No podía enviar el presupuesto: faltaba almacén. | ES Company no tenía almacén. | Creé uno en Inventario y lo seleccioné en el pedido. ([Aviso](capturas/aviso-envio-2.png)) |

## Uso de IA

He usado ChatGPT para resolver algunas dudas y revisar la configuración.
