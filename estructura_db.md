# 🧱 Estructura de Base de Datos SACINV

## Tabla Marca

**Descripción:** Almacena las marcas de los productos.

| Campo | Descripción |
|-------|-------------|
| id_marca | Identificador único de la marca |
| descripcion_marca | Nombre o descripción de la marca |
| creado_por | Usuario del sistema que creó el registro (FK a usuario_sistema.id_us) |
| fecha_creacion | Fecha en la que se creó el registro |
| actualizado_por | Usuario que realizó la última actualización (FK a usuario_sistema.id_us) |
| fecha_actualizacion | Fecha en que se actualizó el registro |
| status_marca | Indica si la marca está habilitada (1) o deshabilitada (0) |

## Tabla Categoría

**Descripción:** Contiene las categorías generales para clasificar las subcategorias.  
**Ejemplo:** Tecnología, Belleza, Papeleria...

| Campo | Descripción |
|-------|-------------|
| id_categoria | Identificador único de la categoría |
| descripcion_categoria | Nombre o descripción de la categoría |
| creado_por | Usuario que creó el registro (FK a usuario_sistema.id_us) |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro (FK a usuario_sistema.id_us) |
| fecha_actualizacion | Fecha de actualización del registro |
| status_categoria | Indica si la categoría está habilitada (1) o deshabilitada (0) |

## Tabla Subcategoría

**Descripción:** Contiene las subcategorías a la que pertenece cada producto.  
**Ejemplo:** Lápiz, Tajalápiz, Borrador... 

| Campo | Descripción |
|-------|-------------|
| id_subctg | Identificador único de la subcategoría |
| descripcion_subctg | Nombre o descripción de la subcategoría |
| creado_por | Usuario que creó el registro (FK a usuario_sistema.id_us) |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro (FK a usuario_sistema.id_us) |
| fecha_actualizacion | Fecha de actualización del registro |
| fk_categoria | Referencia a la categoría principal |
| status_subctg | Indica si la categoría está habilitada (1) o deshabilitada (0) |

## Tabla Tag

**Descripción:** Se registran las etiquetas que un producto que puede ser catalogado. Un producto puede tener muchas etiquetas.  
**Ejemplo:** Lápiz, Mirado, HB

| Campo | Descripción |
|-------|-------------|
| id_tag | Identificador único de la etiqueta |
| nombre_tag | Nombre o descripción de la etiqueta |
| creado_por | Usuario que creó el registro (FK a usuario_sistema.id_us) |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro (FK a usuario_sistema.id_us) |
| fecha_actualizacion | Fecha de actualización del registro |
| status_tag | Indica si la etiqueta está habilitada (1) o deshabilitada (0) |

## Tabla Producto_Tag

**Descripción:** Tabla pivote de la relación de muchos a muchos entre las tablas producto y tag. Por tal motivo solo se colocarán los id de cada tabla.

| Campo | Descripción |
|-------|-------------|
| id_producto_tag | Identificador único de la tabla |
| fk_producto |Llave foránea del producto |
| fk_tag | Llave foránea de la etiqueta |
| creado_por | Usuario que creó el registro (FK a usuario_sistema.id_us) |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro (FK a usuario_sistema.id_us) |
| fecha_actualizacion | Fecha de actualización del registro |

## Tabla Producto

**Descripción:** Registra la información detallada de cada producto.

| Campo | Descripción |
|-------|-------------|
| id_producto | Identificador único del producto |
| descripcion_producto | Nombre del producto |
| observaciones_producto | Información funcional para uso interno sobre el producto |
| stock_minimo | Cantidad mínima de stock para generar compras s |
| tipo | Solo puede contener dos valores P = Producto o S = Servicio |
| fk_marca | Referencia a la marca del producto |
| fk_subcategoria | Referencia a la subcategoría del producto |
| status_producto | Indica si el producto está habilitado (1) o deshabilitado (0) |

>[!NOTE]
>
>El campo **tipo** es de suma importancia ya que si es un servcio, este solo se tendrá en cuenta en las ventas, pero no tendrá ninguna implicación en los inventarios y compras. Nunca generará registros en movimiento_inventario, inventario_capas. No obstante solamente en las ventas es importante hacer el seguimiento.
>El campo tipo se debe restringir de tipo check así:
>CHECK (tipo IN ('P','S'))

## Tabla Tipo_presentacion

**Descripción:** Almacena el catálogo de los tipos de presentación disponibles en el sistema (como Unidad, Caja, Paquete), permitiendo estandarizar y clasificar las distintas formas en que se pueden agrupar o comercializar los productos.

| Campo                | Descripción                                                               |
| -------------------- | ------------------------------------------------------------------------- |
| id_tipo_presentacion | Identificador único del tipo de presentación                              |
| nombre_tipo          | Nombre del tipo de presentación (Ej: Unidad, Caja, Paquete)               |
| status_tipo          | Indica si el tipo de presentación está habilitado (1) o deshabilitado (0) |
| creado_por           | Usuario que creó el registro (FK a usuario)                               |
| fecha_creacion       | Fecha en la que se creó el registro                                       |
| actualizado_por      | Usuario que realizó la última actualización (FK a usuario)                |
| fecha_actualizacion  | Fecha en la que se actualizó el registro                                  |

>[!NOTE]
>Es necesario evitar la duplicación de la misma presentación para un producto con el siguie nte constraint
>```SQL
>UNIQUE (fk_producto, fk_presentacion)
>```

## Tabla Presentacion

**Descripción:** Define las presentaciones específicas basadas en un tipo de presentación, indicando la cantidad de unidades que contiene cada una (por ejemplo, Caja x 12, Paquete x 60). Permite reutilizar configuraciones estándar de empaques y asociarlas posteriormente a múltiples productos.

| Campo                | Descripción                                                          |
| -------------------- | -------------------------------------------------------------------- |
| id_presentacion      | Identificador único de la presentación                               |
| fk_tipo_presentacion | Referencia al tipo de presentación (FK a Tipo_presentacion)          |
| nombre_presentacion  | Nombre descriptivo de la presentación (Ej: Caja x 12, Paquete x 60)  |
| cantidad_unidades    | Cantidad de unidades que contiene la presentación (Ej: 12, 60)       |
| status_presentacion  | Indica si la presentación está habilitada (1) o deshabilitada (0)    |
| creado_por           | Usuario que creó el registro (opcional, FK a usuario)                |
| fecha_creacion       | Fecha en la que se creó el registro                                  |
| actualizado_por      | Usuario que realizó la última actualización (opcional, FK a usuario) |
| fecha_actualizacion  | Fecha en la que se actualizó el registro                             |

## Tabla Producto_presentacion

**Descripción:** Relaciona cada producto con sus diferentes presentaciones disponibles, estableciendo el precio de venta y configuraciones específicas para cada una. Permite definir cómo se comercializa un producto en distintas cantidades o empaques dentro del sistema.

| Campo                        | Descripción                                                                    |
| ---------------------------- | ------------------------------------------------------------------------------ |
| id_producto_presentacion     | Identificador único del registro                                               |
| fk_producto                  | Referencia al producto (FK a producto)                                         |
| fk_presentacion              | Referencia a la presentación (FK a Presentacion)                               |
| precio_venta                 | Precio de venta para esa presentación específica                               |
| presentacion_default         | Indica si es la presentación principal del producto (1 = sí, 0 = no)           |
| status_producto_presentacion | Indica si la presentación del producto está habilitada (1) o deshabilitada (0) |
| creado_por                   | Usuario que creó el registro (opcional, FK a usuario)                          |
| fecha_creacion               | Fecha en la que se creó el registro                                            |
| actualizado_por              | Usuario que realizó la última actualización (opcional, FK a usuario)           |
| fecha_actualizacion          | Fecha en la que se actualizó el registro                                       |

## Tabla Producto_Precio

**Descripción:** Registra la información del histórico de precios de cada producto.

| Campo | Descripción |
|-------|-------------|
| id_producto_precio | Identificador único del producto |
| fk_producto | llave foránea del producto |
| precio_venta_producto | Valor de venta por defecto del producto |
| precio_compra_referencia | Valor de la compra para calcular la ganancia |
| valor_descuento_producto | Valor de descuento aplicado durante temporadas especiales |
| fecha_inicio | Fecha en la que se registra un nuevo precio (Se crea al mismo tiempo que la creación del registro)|
| fecha_final | Fecha de duración del precio (Se actualiza de null a la nueva fecha cuando existe un nuevo precio del mismo producto y es el equivalente a la fecha de inicio de la siguiente creación del registro del precio)|
| creado_por | Usuario que creó el registro (FK a usuario_sistema.id_us) |
| actualizado_por | Usuario que actualizó el registro (FK a usuario_sistema.id_us) |
| fecha_creacion | Fecha de creación del registro (Cuenta como fecha de inicio del precio y como creación del registro)|
| fecha_actualizacion | Fecha de actualización del registro |

>[!NOTE]
>Se debe garantizar la fecha_final se igual o superior a la fecha_inicio así:
>CHECK (fecha_final IS NULL OR fecha_final > fecha_inicio)

## Tabla Promocion

**Descripción:** Solo registra el nombre de las promociones según las temporadas de ventas.

| Campo | Descripción |
|-------|-------------|
| id_promocion | Identificador único de la promoción |
| nombre_promocion |  |
| creado_por | Usuario que creó el registro (FK a usuario_sistema.id_us) |
| actualizado_por | Usuario que actualizó el registro (FK a usuario_sistema.id_us) |
| fecha_creacion | Fecha de creación del registro|
| fecha_actualizacion | Fecha de actualización del registro |

## Tabla Producto_Promoción

**Descripción:** Se registra las promociones que existen tales como temporada escolar o descuento de comfaboy entre otras.

| Campo | Descripción |
|-------|-------------|
| id_producto_promocion | Identificador único del producto |
| fk_producto | llave foránea del producto |
| fk_promocion | llave foránea de la promoción |
| valor_descuento_producto | Valor de descuento aplicado durante temporadas especiales |
| creado_por | Usuario que creó el registro (FK a usuario_sistema.id_us) |
| actualizado_por | Usuario que actualizó el registro (FK a usuario_sistema.id_us) |
| fecha_creacion | Fecha de creación del registro (Cuenta como fecha de inicio del precio y como creación del registro)|
| fecha_actualizacion | Fecha de actualización del registro |

## Tabla Pendiente_compra

**Descripción:** Guarda las compras pendientes generadas por bajo stock o por solicitud de ampliar el stock

| Campo | Descripción |
|-------|-------------|
| id_pendiente | Identificador único de la compra pendiente |
| fk_producto | Referencia al producto pendiente (FK a producto.id_prod) |
| fk_proveedor | Referencia al proveedor que se desea solicitar, puede ser null |
| fecha_pendiente | Fecha desde la cual está pendiente la compra |
| cant_pendiente | Cantidad que se debe comprar al proveedor |
| estado_pendiente | ENUM('PENDIENTE','EN_PROCESO','COMPRADO','CANCELADO') |
| origen_pendiente | ENUM('STOCK_MINIMO','MANUAL') |
| observaciones | Se especifica el motivo del estado del producto a solicitar ya que es posible generar el pendiente y luego cancelarlo |
>[!NOTE]
>El campo origen_pend se utiliza para especificar si el pendiente de la compra se originó por bajo stock o sencillamente se decidió solicitar más producto teniendo sufieciente stock
>
>Se deben evitar la duplicidad de la misma solicitud del producto que se encuentre en PENDIENTE o EN PROCESO, según el estado, ya que si se puede duplicar cuando el estado es COMPRADO o CANCELADO
>CREATE UNIQUE INDEX unique_pendiente_activo
>ON pendiente_compra (fk_producto)
>WHERE estado_solicitud IN ('PENDIENTE','EN_PROCESO');

## Tabla Solicitud_producto

**Descripción:** Hace referencia a la anotación de nuevos productos que no existen en el inventario y que se desea traer.

| Campo | Descripción |
|-------|-------------|
| id_solicitud | Identificador único de la solicitud|
| fk_proveedor | Llave foránea del proveedor, puede ser null|
| descripcion_producto |  |
| cant_solicitud | Cantidad que se debe comprar al proveedor |
| estado_solicitud | ENUM('PENDIENTE','APROBADO','COMPRADO','RECHAZADO') |
| fk_producto | llave foránea del producto, puede ser null |
| prioridad | ENUM(ALTA, MEDIA, BAJA) |
| observaciones | Se especifica el motivo del estado del producto a solicitar ya que es posible generar el pendiente y luego cancelarlo |
| creado_por | llave foránea del usuario |
| fecha_creacion |  |
| aprobado_por | llave foránea del usuario |
| fecha_abprobacion |  |
| actualizado_por | llave foránea del usuario |
| fecha_actualización |  |

>[!NOTE]
>Teniendo en cuenta que la primera vez que se genera el registro no se ha creado el producto en la base de datos, una vez sea COMPRADO se debe Actualizar el id del producto, junto con el id del proveedor.

## Tabla Producto_img_video
**Descripción:** Guarda los nombres de las imágenes y videos del producto.

| Campo | Descripción |
|-------|-------------|
| id_archivo | Identificador único del registro |
| nombre_archivo | Nombre del archivo multimedia |
| tipo_archivo_prodiv | Tipo de archivo (imagen o video) |
| fk_producto | Referencia al producto relacionado |

## Tabla Producto_codigo
**Descripción:** Un mismo tipo de producto puede tener varios códigos de barra y por ende varios códigos manuales, sobretodo marcas blancas. El software mostrará en pantalla las opciones encontradas con el mismo código en caso de repetirse con la de algún otro producto. Ya que varios proveedores manejan su propio sistema de códigos de barra.

| Campo | Descripción |
|-------|-------------|
| id_codigo | Identificador único del código |
| codigo_barras | Código de barras del producto (pueden existir varios) |
| codigo_manual | Últimos 6 caracteres del código de barras (usado como identificación manual) |
| fk_producto | Referencia al producto |

## Tabla Producto_oferta
**Descripción:** Las ofertas son aquellas que representan un valor menor del producto a partir de una cantidad mínima de venta.    
**Ejemplo:** 12 lápices normalmente se vendería en $12.000, sin embargo por la cantidad se puede realizar un pequeño descuento, y cuya venta puede darse en $10.000.

| Campo | Descripción |
|-------|-------------|
| id_oferta | Identificador único de la oferta |
| fk_producto | Referencia al producto |
| cant_oferta | Cantidad mínima para aplicar el precio en oferta |
| valor_venta_oferta | Precio de venta unitario durante la oferta |
| status_oferta | Indica si la oferta está habilitada (1) o deshabilitada (0) |

## Tabla Ubicacion
**Descripción:** Se registra el nombre de las ubicaciones con las que cuenta la empresa para almacenar los productos.  
**Ejemplo:** Bodega 1, Bodega 2, Almacén

| Campo | Descripción |
|-------|-------------|
| id_ubicacion | Identificador único de ubicación |
| nombre_ubicacion | Nombre del lugar donde se almacena el producto (unique) |
| ubicacion_default | Indica si es la ubicación que cargará por defecto en el formulario |
| creado_por | Usuario que creó el registro |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro |
| fecha_actualizacion | Fecha de actualización del registro |
| status_ubicacion | Indica si la ubicación está habilitada (1) o deshabilitada (0) |

## Tabla Snapshot_ubicacion
**Descripción:** Es una tabla caché para almacenar y actualizar en un mismo registro la cantidad existente de un producto en cierta ubicación, va de la mano con la tabla Movimiento_inventario. Se actualiza en cada movimiento. 
**Ejemplo:** 200 Lapices Mirado en Bodega 1, 25 Lapices Mirado en Almacén  

| Campo | Descripción |
|-------|-------------|
| id_produb | Identificador único |
| fk_producto | Referencia al producto |
| fk_ubicacion | Referencia al lugar de ubicación |
| cant_produb | Cantidad del producto en esa ubicación |

>[!NOTE]
>Se debe evitar duplicadosen los que se repiten llaves foráneas en el mismo registro:
>
>ALTER TABLE snapshot_ubicacion
>ADD CONSTRAINT unique_producto_ubicacion
>UNIQUE (fk_producto, fk_ubicacion);

## Tabla Departamento
**Descripción:** Almacena los nombres de los departamentos de Colombia

| Campo | Descripción |
|-------|-------------|
| id_depart | Identificador del departamento |
| nombre_depart | Nombre del departamento |

## Tabla Ciudad
**Descripción:** Almacena los nombres de los municipios y ciudades que pertenencen a los departamentos de Colombia.

| Campo | Descripción |
|-------|-------------|
| id_ciudad | Identificador de la ciudad |
| nombre_ciudad | Nombre de la ciudad |
| fk_depart | Referencia al departamento |

## Tabla Proveedor

| Campo | Descripción |
|-------|-------------|
| id_proveedor | Identificador del proveedor |
| nit_proveedor | NIT del proveedor |
| razon_social_proveedor | Razón social del proveedor |
| email_proveedor | Correo electrónico del proveedor |
| direccion_proveedor | Dirección del proveedor |
| status_proveedor | Indica si el proveedor está habilitado (1) o deshabilitado (0) |
| fk_ciudad | Referencia a la ciudad del proveedor |

## Tabla Telefono_proveedor

**Descripción:** Por lo general un proveedor tiene varios teléfonos y es necesario guardarlos todos

| Campo | Descripción |
|-------|-------------|
| id_tel_proveedor | Identificador del telefono |
| numero_tel_proveedor | Número de teléfono |
| whatsapp_tel_proveedor | Si el número está registrado en whatsapp (1) sino (0) |
| fk_proveedor | Referencia a proveedor |
| status_tel_proveedor | Indica si el numero teléfónico está habilitado (1) o deshabilitado (0) |

## Tabla Metodo_pago

| Campo | Descripción |
|-------|-------------|
| id_metodo_pago | Identificador del método de pago |
| descipcion_metodo_pago | Descripción del método de pago |
| status_metodo_pago | Indica si el método está habilitado (1) o deshabilitado (0) |

## Tabla Compra_master

**Descripción:** Almacena los datos generales de una compra, pero la relación de productos comprados, se realiza en otra tabla llamada *Compra_detalle*

| Campo | Descripción |
|-------|-------------|
| id_compra_master | Identificador de la compra |
| fk_proveedor | Referencia al proveedor |
| nombre_adjunto_compra_master | Nombre del archivo adjunto guardado (factura) |
| fecha_compra_master | Fecha de la compra |
| total_descuento | Monto total del descuento aplicable |
| total_compra_master | Total general de la compra |
| observaciones_compra_master | Observaciones sobre la compra |
| creado_por | Usuario que creó el registro |
| fecha_creacion | Fecha de creación de la compra |
| actualizado_por | Usuario que actualizó el registro |
| fecha_actualizacion | Fecha de actualización de la compra |
| estado_compra_master | Estado de la compra (Registrada, Pagada, Anulada) |

## Tabla Compra_detalle

**Descripción:** Relaciona todos los productos comprados que pertenezcan a la tabla *Compra_Master*

| Campo | Descripción |
|-------|-------------|
| id_compra_detalle | Identificador del detalle de compra |
| fk_compra_master | Referencia a compra_master |
| fk_producto | Referencia al producto comprado |
| cant_compra_detalle | Cantidad de producto comprado |
| valor_unit_compra_detalle | Valor unitario del producto |
| xje_desc_compra_detalle | Porcentaje de descuento ofrecido por el proveedor |
| descuento_unit_compra_detalle | Valor del descuento generado |
| total_compra_detalle | Total del detalle (cant_compra_detalle * valor_unit_compra_detalle) |
| valor_venta_compra_detalle | Valor de venta calculado del producto |
| fecha_vencimiento_compra_detalle | Fecha de vencimiento del producto (si aplica) |

## Tabla Abono_compra

**Descripción:** Esta tabla almacena los diferentes nombres de los archivos adjuntos que son comprobantes de abonos realizados o pago total. Según esta tabla se puede saber la cantidad de veces que ha abonado al proveedor sobre la misma factura 

| Campo | Descripción |
|-------|-------------|
| id_abono_compra | Identificador del abono |
| movimiento_abono_compra | Movimiento realizado (Abonó(A) - Devolución(D) - Cancelado(C)) |
| monto_abono_compra | Valor abonado o pagado |
| nombre_comprobante_abono_compra | Nombre del archivo de comprobante de pago (.jpg) |
| fecha_hora_abono_compra | Fecha y hora (Diligenciado por el usuario, sin embargo el sistema le sugiere la fecha y hora actual del tiempo real)|
| fk_metodo_pago | Referencia al método de pago |
| fk_compra_master | Referencia a la compra_master |
| observaciones_abono_compra | Observaciones |

## Tabla Devolucion_compra

**Descripción:** Esta tabla relaciona los productos que se devuelven al proveedor con su respectiva justificación.

| Campo | Descripción |
|-------|-------------|
| id_devolucion_compra | Identificador de la devolución |
| fk_compra_detalle | Llave foránea de la factura Compra Detalle para obtener datos no solo del producto, si no datos adicionales de la compra master
| fecha_hora_devolucion_compra | Fecha de la devolución |
| cant_devolucion_compra | Cantidad devuelta del producto |
| estado_devolucion_compra | (0) Si está pendiente (1) si ya se realizó la devolución |
| observaciones_devolucion_compra | Justificación de la devolución |

## Tabla Usuario

| Campo | Descripción |
|-------|-------------|
| id_usuario_sistema | Identificador del usuario |
| nombre_usuario_sistema | Nombre del usuario |
| nickname_usuario_sistema | Usuario de acceso |
| password_usuario_sistema | Contraseña de acceso |
| tel_usuario_sistema | Teléfono del usuario |
| dir_usuario_sistema | Dirección del usuario |
| email_usuario_sistema | Correo electrónico del usuario |
| token_usuario_sistema | Token para activar la cuenta o recuperar la contraseña |
| fk_ciudad | Ciudad del usuario |
| status_usuario_sistema | Indica si el usuario está habilitado (1) o deshabilitado (0) |

## Tabla Cliente
**Descripción:** Almacena clientes tanto corporativos como particulares

| Campo | Descripción |
|-------|-------------|
| id_cliente | Identificador del cliente |
| cedula_nit_cliente | Cédula o NIT del cliente |
| razon_social_cliente | Nombre o razón social del cliente |
| tel_cliente | Teléfono del cliente |
| direccion_cliente | Dirección del cliente |
| email_cliente | Correo electrónico del cliente |
| tipo_cliente | Es un cliente Particular(P) o Corporativo(C) |
| fk_ciudad | Referencia a la tabla Ciudad |

## Tabla Empleado_cliente

**Descripción:** Registra los nombres de los empleados que trabajan para los clientes corporativos que solicitan los productos. Pensado en la trazabilidad de las solicitudes en compras a cŕedito.

| Campo | Descripción |
|-------|-------------|
| id_empleado_cliente | Identificador del empleado del cliente |
| fk_cliente | Referencia al cliente corporativo |
| cedula_empleado_cliente | Cédula del empleado |
| nombre_empleado_cliente | Nombre del empleado |
| tel_empleado_cliente | Teléfono del empleado |

## Tabla Venta_master

**Descripción:** Al igual que la tabla *Compra_master*, almacena los datos generales de la Venta

| Campo | Descripción |
|-------|-------------|
| id_venta_master | Identificador de la venta |
| numero_venta_master | Número consecutivo de venta al expedir un recibo |
| fk_cliente | Referencia al cliente |
| fecha_hora | Fecha de la factura |
| subtotal | Suma total de los registros vendidos |
| total_descuento | Suma total de descuentos |
| total_venta | Valor total después del descuento |
| saldo_pendiente | es distinto a 0 en caso de no pagar la totalidad de la factura |
| observaciones | Observaciones de la venta |
| estado_factura | ENUM('PENDIENTE','PAGADA','ANULADA') |
| creado_por | Usuario que actualizó el registro |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro |
| fecha_actualizacion | Fecha de actualización del registro |

## Tabla Venta_detalle

**Descripción:** Se relaciona el detalle de cada producto vendido al cliente, la razón por la cual se relaciona el usuario en esta tabla se debe a las ventas a *crédito* que se pueden realizar a un cliente en diferentes fechas, y por lo tanto, pudo venderse el producto por empleados diferentes.

| Campo | Descripción |
|-------|-------------|
| id_venta_detalle | Identificador del detalle de venta |
| fk_venta_master | Referencia a venta_master |
| fk_producto | Referencia al producto vendido |
| fk_empleado_cliente | Referencia al empleado del cliente |
| creado_por | Usuario que creó el registro |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro |
| fecha_actualizacion | Fecha de actualización del registro |
| cant_venta_detalle | Cantidad vendida |
| valor_unit_venta_detalle | Valor unitario vendido |
| total_venta_detalle | Total del detalle |

## Tabla Devolucion_venta

**Descripción:** Esta tabla relaciona los productos que se devuelven por parte del cliente con su respectiva justificación.

| Campo | Descripción |
|-------|-------------|
| id_devolucion_venta | Identificador de la devolución |
| fk_venta_detalle | Llave foránea de la factura Venta Detalle para obtener datos no solo del producto, si no datos adicionales de la venta master
| fecha_hora_devolucion_venta | Fecha de la devolución |
| cant_devolucion_venta | Cantidad devuelta del producto |
| observaciones_devolucion_venta | Justificación de la devolución |

## Tabla Abono_venta
**Descripción:** Esta tabla almacena los diferentes nombres de los archivos adjuntos que son comprobantes de abonos realizados o pago total. Según esta tabla se puede saber la cantidad de veces que ha abonado un cliente a la misma factura 

| Campo | Descripción |
|-------|-------------|
| id_abono_venta | Identificador del pago |
| movimiento_abono_venta | ENUM('PAGO','DEVOLUCION') La Devolución implica cuando el cliente devuelve el producto y se devuelve el pago o abono realizado|
| valor_recibido | Dinero recibido por parte del cliente |
| valor_aplicado | puede ser tanto el valor recibido si es menor o igual al saldo de la venta total, o el valor del saldo restante cuando el valor recibido es mayor a al saldo |
| valor_cambio | Dinero entregado al cliente |
| comprobante_abono_venta | Nombre del comprobante de pago (.jpg o .pdf)|
| fecha_hora_abono_venta | Fecha y hora del pago |
| fk_metodo_pago | Referencia al método de pago |
| fk_venta_master | Referencia a la venta master |
| observaciones_abono_venta | Observaciones del pago |

## Tabla Movimiento_inventario
**Descripción:** Se realizarán los 3 inventarios LIFO FIFO Y PONDERADO

| Campo | Descripción |
|-------|-------------|
| id_inventario | Identificador del movimiento |
| fk_producto | Referencia al producto |
| tipo_inventario | será de tipo enum (COMPRA (C), VENTA (V), DEVOLUCION_CLIENTE (DC), DEVOLUCION_PROVEEDOR (DP), AJUSTE_POSITIVO (AP), AJUSTE_NEGATIVO (AN), INVENTARIO_INICIAL (IN)) |
| cant_inventario | Cantidad del movimiento |
| valor_unit_inventario | Valor unitario (solo para entradas) para salidas se utiliza null, ya que se calcula de acuerdo al tipo de inv|
| fecha_hora_inventario | Fecha y hora del movimiento |
| fk_compra_detalle | Referencia al detalle de compra, debe permitir valores null|
| fk_venta_detalle | Referencia al detalle de venta, debe permitir valores null|
| fk_ubicacion | Referencia a la tabla ubicación|
| id_grupo_movimiento | Se usa para agrupar movimientos que pertenecen a una misma operación (compra distribuida, venta, traslado, ajuste, etc.) |
| observaciones | En caso de haber devoluciones, ajustes, traslados, se debe especificar la razón por la que se dió este movimiento|

>[!NOTE]
>
>No se relaciona la llave foránea del usuario ya que es una tabla que se alimenta automáticamente de otras tablas que estaría diligenciando el usuario final, sin embargo es el corazón del software.
>
>Las opciones ajuste positivo (AP) y ajuste negativo (AN) se utilizará para dos fines, ya sea por encontrar productos o pérdida de de los mismos, O para traslados de mercancia entre dos ubicaciones, esa especificación irá en el campo observaciones, en el cual se deben mostrar sugerencias de llenado.
>
>id_grupo_movimiento es un número incremental que se repetirá unicamente entre traslados
>
>tipo_inventario se debe restringir con *check* así:
>ALTER TABLE movimiento_inventario
>ADD CONSTRAINT chk_tipo_inventario
>CHECK (tipo_inventario IN ('C','V','DC','DP','AP','AN','IN'));
>
>El campo valor_unit_inventario debe cumplir las siguientes reglas:
>| Tipo               | valor_unit |
>| ------------------ | ---------- |
>| Compra             | ✔          |
>| Inventario inicial | ✔          |
>| Devolución cliente | ✔          |
>| Venta              | ❌ NULL     |
>| Salida traslado    | ❌ NULL     |
>
>El campo id_grupo_movimiento es obligatorio en los siguientes movimientos:
>| Tipo de operación                            | ¿Usa grupo? |
>| -------------------------------------------- | ----------- |
>| Compra simple (1 ubicación)                  | ❌           |
>| Compra distribuida                           | ✅           |
>| Venta simple                                 | ❌           |
>| Venta desde varias ubicaciones               | ✅           |
>| Traslado                                     | ✅           |
>| Ajuste simple                                | ❌           |
>| Ajuste masivo (varias ubicaciones/productos) | ✅           |
>
>Otro ajuste necesario es la restricción de los valores que se aceptan en el tipo_movimiento y las llaves foráneas así:
>CHECK (
>  (tipo_inventario = 'C' AND fk_compra_detalle IS NOT NULL)
>  OR
>  (tipo_inventario = 'V' AND fk_venta_detalle IS NOT NULL)
>  OR
>  (tipo_inventario IN ('DC','DP','AP','AN','IN'))
>)
>Si es una compra (C), debe venir de compra_detalle, pero si es una venta (V), debe venir de venta_detalle

## Tabla Inventario_capas
**Descripción:** Tiene como objetivo controlar las salidas de cada capa, ya que el costo puede variar con el tiempo, y es necesaria para determinar el valor real del inventario de cada producto.

| Campo | Descripción |
|-------|-------------|
| id_capa | Identificador del movimiento |
| fk_producto | Llave foránea del producto |
| fk_movimiento_inventario | Llave foránea del Movimiento_inventario |
| cant_inicial | Total de productos ingresados al momento de la entrada ya sea Inventario Inicial o Compras |
| cant_restante | Inicialmente inicia con el mismo valor que la cant_inicial y se irá restando (actualizando el registro) por cada salida que se presente |
| costo_unitario | costo de la compra |
| fecha_capa | Fecha de la entrada |
| status_capa | Solo contendrá dos valores A=Activa o C=Cerrada, solo se cerrará cuando cant_restante sea igual a 0, para realizar filtros y operaciones más rápidas |

## Tabla Inventario_salida_detalle
**Descripción:** Registra el detalle del consumo de inventario por capas para cada venta, 
permitiendo identificar el costo real de los productos vendidos según el método de costeo (FIFO, o Ponderado).
| Campo | Descripción |
|-------|-------------|
| id_salida_detalle | Identificador de la salida|
| fk_venta_detalle  | Llave foránea de la tabla venta_detalle |
| fk_capa           | Llave foránea de la tabla inventario_capas |
| fk_producto       | Llave foránea de la tabla producto (para agilizar consultas) |
| cantidad_salida   | cantidad vendida |
| costo_unitario    | costo unitario proveniente de la capa |
| subtotal_costo    | multiplicación de la cantidad_salida x costo_unitario |
| fecha_registro    | Tipo de dato: TIMESTAMP DEFAULT CURRENT_TIMESTAMP |

>[!NOTE]
>APLICAR LAS SIGUIENTES REGLAS DE INTEGRIDAD
>```SQL
>CHECK (cantidad_salida > 0),
>CHECK (costo_unitario >= 0),
>CHECK (subtotal_costo = cantidad_salida * costo_unitario)
>```
>

## Tabla Kardex_fifo
**Descripción:** Mantiene actualizado el inventario FIFO

| Campo | Descripción |
|-------|-------------|
| id_kardex_fifo | id de la tabla |
| fk_inventario | Referencia al id del inventario para obtener datos de las otras entidades como producto, compra_detalle, venta_detalle |
| cant_entrada | Cantidad que ingresa |
| cant_salida | Cantidad que egresa |
| cant_saldo | Cantidad restante |
| valor_saldo | Valor actual del inventario |
| fecha_movimiento | Fecha del movimiento |

## Tabla Kardex_ponderado
**Descripción:** Mantiene actualizado el inventario PONDERADO

| Campo | Descripción |
|-------|-------------|
| id_kardex_ponderado | id de la tabla |
| fk_inventario | Referencia al id del inventario para obtener datos de las otras entidades como producto, compra_detalle, venta_detalle |
| cant_entrada | Cantidad que ingresa |
| cant_salida | Cantidad que egresa |
| cant_saldo | Cantidad restante |
| valor_saldo | Valor actual del inventario |
| fecha_movimiento | Fecha del movimiento |

## Tabla Snapshot_inventario
**Descripción:** Registra el corte mensual de cada uno de los inventarios de los productos para evitar consultas lentas en la tabla *Inventario_Movimiento*

| Campo | Descripción |
|-------|-------------|
| id_snapshot | Identificador del corte del inventario |
| fecha_corte_snapshot | Fecha del corte es la misma fecha de creación |
| fk_producto_snapshot | Referencia del producto |
| cant_final_snapshot | cantidad final del producto |
| costo_lifo_snapshot | Costo final del inventario LIFO |
| costo_ponderado_snapshot | Costo final del inventario Ponderado |

## Tabla Stock_actual
**Descripción:** Se basa en la cantidad del stock actual de cada producto basado en la tabla llamada Movimiento_inventario, con el fin de obtener el saldo de cada producto en tiempo real

| Campo | Descripción |
|-------|-------------|
| id_stock | Identificador del registro |
| fk_producto | Referencia al producto |
| cant_stock | Cantidad actual del producto |

## Tabla Modulo
**Descripción:** Almacena el nombre de cada uno de los módulos visibles para el usuario
| Campo | Descripción |
|-------|-------------|
| id_modulo | Identificador del módulo |
| nombre_modulo | Nombre del módulo |

## Tabla Permisos_Usuario_Modulo
**Descripción:** Almacena la relación de los permisos de tiene cada usuario con respecto a cada uno de los módulos visible en el software web

| Campo | Descripción |
|-------|-------------|
| id_permiso | Identificador del registro |
| fk_usuario | Referencia al usuario |
| fk_modulo | Referencia a al módulo |
| lectura_registro | Permiso para leer registros |
| crear_registro | Permiso para crear registros |
| actualizar_registro | Permiso para actualizar registros |
| eliminar_registro | Permiso para eliminar registros |

## Tabla Datos_empresa
**Descripción:** Almacena los datos de la empresa que hace uso del software para mostrarlo en los reportes.

| Campo | Descripción |
|-------|-------------|
| id_de | Identificador del registro |
| nit_de | Nit de la empresa |
| razon_social_de | Razón social de la empresa |
| slogan_de | Frase utilizada por la empresa para conectar con los clientes |
| regimen_de | Tipo de régimen |
| direccion_de | Dirección |
| tel_de | Teléfono de la empresa |
| whatsapp_de | Whatsapp de la empresa |
| email_de | Email de la empresa |
| logo_de | Nombre de la imagen de la empresa que carga en los informes |
| xje_venta_de | Indica cual es el porcentaje de venta para que el sistema calcule de forma autormática al momento de realizar una compra |
| fk_usuario | Referencia al usuario |
| creado_por | Usuario que creó el registro |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro |
| fecha_actualizacion | Fecha de actualización del registro |

# Recomendaciones para crear la base de datos:
* Creación de índices propuestos:
   
   ### Movimiento_inventario:
   **Objetivo:** Esto acelera consultas como movimientos de un producto ordenados por fecha
   
   ```SQL
   CREATE INDEX idx_mov_producto_fecha
   ON movimiento_inventario (fk_producto, fecha_hora_inventario);

   CREATE INDEX idx_mov_grupo
   ON movimiento_inventario (id_grupo_movimiento);
   ```

   ### Inventario_capas:
   **Objetivo:** Esto permite buscar rápidamente capas activas del producto.
   
   ```SQL
   CREATE INDEX idx_capas_producto_fecha
   ON inventario_capas (fk_producto, fecha_capa);

   CREATE INDEX idx_capa_producto
   ON inventario_capas (fk_producto, status_capa);
   ```
   
   ### Venta_detalle:
   **Objetivo:** Para consultar el historial de ventas de un proeucto
   
   ```SQL
   CREATE INDEX idx_venta_producto
   ON venta_detalle (fk_producto);
   ```
   
   ### Compra_detalle:
   **Objetivo:** Para consultar el historial de compras de un proeucto
   
   ```SQL
   CREATE INDEX idx_compra_producto
   ON compra_detalle (fk_producto);
   ```
   
   ### Producto_codigo:
    
   ```SQL
   CREATE INDEX idx_codigo_barras
   ON producto_codigo (codigo_barras);
   
   CREATE INDEX idx_codigo_manual
   ON producto_codigo (codigo_manual);
   ```
   
   ### Producto_tag:
   **Objetivo:** Para acelerar búsquedas por etiqueta
   
   ```SQL
   CREATE INDEX idx_producto_tag_producto
   ON producto_tag (fk_producto);

   CREATE INDEX idx_producto_tag_tag
   ON producto_tag (fk_tag);
   ```
   
   ### Snapshot_ubicacion:
   
   ```SQL
   CREATE INDEX idx_snapshot_producto
   ON snapshot_ubicacion (fk_producto);

   CREATE INDEX idx_snapshot_ubicacion
   ON snapshot_ubicacion (fk_ubicacion);

   CREATE INDEX idx_snapshot_lookup
   ON snapshot_ubicacion (fk_producto, fk_ubicacion);
   ```
   
   ### Producto:
   **Objetivo:** Buscar productos por nombre
   
   ```SQL
   CREATE INDEX idx_producto_nombre
   ON producto (descripcion_producto);
   ```
   
   ### Venta_master:
   **Objetivo:** Indice para reportes
   
   ```SQL
   CREATE INDEX idx_venta_fecha
   ON venta_master (fecha_hora_venta_master);
   ```

   ### Abono_venta:
   ```SQL
   CREATE INDEX idx_abono_venta_master
   ON abono_venta (fk_venta_master);
   ```
   
   ### Inventario_salida_detalle:
   ```SQL
   CREATE INDEX idx_salida_venta
   ON inventario_salida_detalle (fk_venta_detalle);

   CREATE INDEX idx_salida_capa
   ON inventario_salida_detalle (fk_capa);

   CREATE INDEX idx_salida_producto
   ON inventario_salida_detalle (fk_producto);
   
   /*ventas por producto y utilidad por día*/
   CREATE INDEX idx_salida_producto_fecha
   ON inventario_salida_detalle (fk_producto, fecha_registro);
   ```
      
   ## Resultado de Indexes:

   | Tabla                     | Índice                             |
   | ------------------------- | ---------------------------------- |
   | movimiento_inventario     | fk_producto, fecha_hora_inventario |
   | inventario_salida_detalle | fk_venta_detalle                   |
   | inventario_salida_detalle | fk_capa                            |
   | inventario_salida_detalle | fk_producto                        |
   | inventario_salida_detalle | fk_producto, fecha_registro        |
   | venta_detalle             | fk_producto                        |
   | abono_venta               | fk_venta_master                    |
   | compra_detalle            | fk_producto                        |
   | producto_codigo           | codigo_barras                      |
   | producto_codigo           | codigo_manual                      |
   | producto_tag              | fk_producto                        |
   | producto_tag              | fk_tag                             |
   | inventario_capas          | fk_producto,status                 |
   | producto_ubicacion        | fk_producto                        |
   | producto_ubicacion        | fk_ubicacion                       |
   | venta_master              | fecha                              |
  
* Crear nuevo archivo markdown para los diagramas de flujo al momento de realizar una compra o venta de un producto. ya que este movimiento toca muchas tablas en secuencia
