# 🧱 Estructura de Base de Datos SACINV

## Brands | Marcas

**Descripción:** Almacena las marcas de los productos.

| Campo                    | Traducción          | Descripción                                                                                                                   |
| ------------------------ | ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| id                       | id                  | Identificador único de la marca  <br> *Unique identifier of the brand*                                                        |
| name                     | nombre              | Nombre o descripción de la marca  <br> *Name or description of the brand*                                                     |
| created_by               | creado_por          | Usuario del sistema que creó el registro  <br> *System user who created the record*                                           |
| updated_by               | actualizado_por     | Usuario que realizó la última actualización  <br> *User who performed the last update*                                        |
| created_at               | fecha_creacion      | Fecha en la que se creó el registro  <br> *Date when the record was created*                                                  |
| updated_at               | fecha_actualizacion | Fecha en la que se actualizó el registro  <br> *Date when the record was last updated*                                        |
| is_active                | estado / activo     | Indica si la marca está Activo (1) o Inactivo (0)  <br> *Indicates whether the brand is Active (1) or Inactive (0)* |

**Descripción:** Contiene las categorías generales para clasificar las subcategorias.  
**Ejemplo:** Tecnología, Belleza, Papeleria...


## Categories | Categorías
| Campo                    | Traducción          | Descripción                                                                                                                         |
| ------------------------ | ------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| id                       | id                  | Identificador único de la categoría <br> *Unique identifier of the category*                                                        |
| name                     | nombre              | Nombre o descripción de la categoría <br> *Name or description of the category*                                                     |
| created_by               | creado_por          | Usuario del sistema que creó el registro <br> *System user who created the record*                                                  |
| updated_by               | actualizado_por     | Usuario que realizó la última actualización <br> *User who performed the last update*                                               |
| created_at               | fecha_creacion      | Fecha en la que se creó el registro <br> *Date when the record was created*                                                         |
| updated_at               | fecha_actualizacion | Fecha en la que se actualizó el registro <br> *Date when the record was last updated*                                               |
| is_active                | estado / activo     | Indica si la categoría está Activa (1) o Inactiva (0) <br> *Indicates whether the category is Active (1) or Inactive (0)* |


## Subcategories | Subcategorías

**Descripción:** Contiene las subcategorías a la que pertenece cada producto.  
**Ejemplo:** Lápiz, Tajalápiz, Borrador... 

| Campo                    | Traducción          | Descripción                                                                                                                               |
| ------------------------ | ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| id                       | id                  | Identificador único de la subcategoría <br> *Unique identifier of the subcategory*                                                        |
| name                     | nombre              | Nombre o descripción de la subcategoría <br> *Name or description of the subcategory*                                                     |
| category_id              | fk_categoria        | Referencia a la categoría principal <br> *Reference to the parent category*                                                               |
| created_by               | creado_por          | Usuario del sistema que creó el registro <br> *System user who created the record*                                                        |
| updated_by               | actualizado_por     | Usuario que realizó la última actualización <br> *User who performed the last update*                                                     |
| created_at               | fecha_creacion      | Fecha en la que se creó el registro <br> *Date when the record was created*                                                               |
| updated_at               | fecha_actualizacion | Fecha en la que se actualizó el registro <br> *Date when the record was last updated*                                                     |
| is_active                | estado / activo     | Indica si la subcategoría está Activo (1) o Inactivo (0) <br> *Indicates whether the subcategory is Active (1) or Inactive (0)* |

## Tags | Etiquetas

**Descripción:** Se registran las etiquetas que un producto que puede ser catalogado. Un producto puede tener muchas etiquetas.  
**Ejemplo:** Lápiz, Mirado, HB

| Campo (Laravel / Inglés) | Traducción          | Descripción                                                                                                                   |
| ------------------------ | ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| id                       | id                  | Identificador único de la etiqueta <br> *Unique identifier of the tag*                                                        |
| name                     | nombre              | Nombre de la etiqueta <br> *Name of the tag*                                                                                  |
| created_by               | creado_por          | Usuario del sistema que creó el registro <br> *System user who created the record*                                            |
| updated_by               | actualizado_por     | Usuario que realizó la última actualización <br> *User who performed the last update*                                         |
| created_at               | fecha_creacion      | Fecha en la que se creó el registro <br> *Date when the record was created*                                                   |
| updated_at               | fecha_actualizacion | Fecha en la que se actualizó el registro <br> *Date when the record was last updated*                                         |
| is_active                | estado / activo     | Indica si la etiqueta está Activo (1) o Inactivo (0) <br> *Indicates whether the tag is Active (1) or Inactive (0)* |

## product_tag | Etiqueta del producto

**Descripción:** pivote de la relación de muchos a muchos entre las tablas producto y tag. Por tal motivo solo se colocarán los id de cada tabla.

| Campo (Laravel / Inglés) | Traducción          | Descripción                                                           |
| ------------------------ | ------------------- | ----------------------------------------------------------------------|
| product_id               | fk_producto         | Llave foránea del producto <br> *Foreign key referencing the product* |
| tag_id                   | fk_tag              | Llave foránea de la etiqueta <br> *Foreign key referencing the tag*   |

>[!NOTE]
> La tabla *product_tag* es una tabla pivote, por lo tanto No necesita id propio, por lo tanto se usa la clave compuesta product_id + tag_id

## Products | Productos

**Descripción:** Registra la información detallada de cada producto.

| Campo (Laravel / Inglés) | Traducción          | Descripción                                                                                                             |
| ------------------------ | ------------------- | ------------------------------------------------------------------------------------------------------------------------|
| id                       | id                  | Identificador único del producto <br> *Unique identifier of the product*                                                |
| name                     | nombre              | Nombre del producto <br> *Product name*                                                                                 |
| internal_notes           | observaciones       | Información interna sobre el producto <br> *Internal notes about the product*                                           |
| minimum_stock            | stock_minimo        | Cantidad mínima de stock para generar compras <br> *Minimum stock level to trigger purchases*                           |
| type                     | tipo                | Tipo de producto: producto o servicio <br> *Product type: product or service*                                           |
| brand_id                 | fk_marca            | Referencia a la marca del producto <br> *Reference to the product's brand*                                              |
| subcategory_id           | fk_subcategoria     | Referencia a la subcategoría del producto <br> *Reference to the product's subcategory*                                 |
| is_active                | estado / activo     | Indica si el producto está Activo (1) o Inactivo (0) <br> *Indicates whether the product is Active (1) or Inactive (0)* |
| created_by               | credo por           | Usuario del sistema que creó el registro <br> *System user who created the record*                                      |
| updated_by               | actualizado por     | Usuario que realizó la última actualización <br> *User who performed the last update*                                   |
| created_at               | fecha_creacion      | Fecha en la que se creó el registro <br> *Date when the record was created*                                             |
| updated_at               | fecha_actualizacion | Fecha en la que se actualizó el registro <br> *Date when the record was last updated*                                   |

>[!NOTE]
>
>El campo *type* es de suma importancia ya que si es un servcio, este solo se tendrá en cuenta en las ventas, pero no tendrá ninguna implicación en los inventarios y compras. Nunca generará registros en movimiento_inventario, inventario_capas. No obstante solamente en las ventas es importante hacer el seguimiento.
>El campo tipo se debe restringir de tipo check así:
>CHECK (tipo IN ('P','S'))

## presentation_types | Tipos de presentacion

**Descripción:** Almacena el catálogo de los tipos de presentación disponibles en el sistema (como Unidad, Caja, Paquete), permitiendo estandarizar y clasificar las distintas formas en que se pueden agrupar o comercializar los productos.

| Campo (Laravel / Inglés) | Traducción          | Descripción                                                                                                       |
| ------------------------ | ------------------- | ----------------------------------------------------------------------------------------------------------------- |
| id                       | id                  | Identificador único del tipo de presentación <br> *Unique identifier of the presentation type*                    |
| name                     | nombre              | Nombre del tipo de presentación (Unidad, Caja, Paquete) <br> *Name of the presentation type (Unit, Box, Package)* |
| is_active                | estado / activo     | Indica si el tipo de presentación está habilitado <br> *Indicates whether the presentation type is enabled*       |
| created_by               | creado_por          | Usuario que creó el registro <br> *User who created the record*                                                   |
| updated_by               | actualizado_por     | Usuario que actualizó el registro <br> *User who updated the record*                                              |
| created_at               | fecha_creacion      | Fecha de creación del registro <br> *Date when the record was created*                                            |
| updated_at               | fecha_actualizacion | Fecha de actualización del registro <br> *Date when the record was last updated*                                  |

## Presentations | Presentaciones

**Descripción:** Define las presentaciones específicas basadas en un tipo de presentación, indicando la cantidad de unidades que contiene cada una (por ejemplo, Caja x 12, Paquete x 60). Permite reutilizar configuraciones estándar de empaques y asociarlas posteriormente a múltiples productos.

| Campo (Laravel / Inglés) | Traducción           | Descripción                                                                                                 |
| ------------------------ | -------------------- | ----------------------------------------------------------------------------------------------------------- |
| id                       | id                   | Identificador único de la presentación <br> *Unique identifier of the presentation*                         |
| presentation_type_id     | fk_tipo_presentacion | Referencia al tipo de presentación <br> *Reference to the presentation type*                                |
| name                     | nombre               | Nombre de la presentación (Caja x 12, Paquete x 60) <br> *Name of the presentation (Box of 12, Pack of 60)* |
| unit_quantity            | cantidad_unidades    | Cantidad de unidades que contiene <br> *Number of units contained in the presentation*                      |
| is_active                | estado / activo      | Indica si la presentación está Activa <br> *Indicates whether the presentation is Active*                   |
| created_by               | creado_por           | Usuario que creó el registro <br> *User who created the record*                                             |
| updated_by               | actualizado_por      | Usuario que actualizó el registro <br> *User who updated the record*                                        |
| created_at               | fecha_creacion       | Fecha de creación del registro <br> *Date when the record was created*                                      |
| updated_at               | fecha_actualizacion  | Fecha de actualización del registro <br> *Date when the record was last updated*                            |

## Product_presentations | Presentaciones de producto

**Descripción:** Relaciona cada producto con sus diferentes presentaciones disponibles, estableciendo el precio de venta y configuraciones específicas para cada una. Permite definir cómo se comercializa un producto en distintas cantidades o empaques dentro del sistema. Ojo pero no guarda el histórico de precios, solo se actualiza el precio actual de acuerdo a la presentación

| Campo (Laravel / Inglés) | Traducción           | Descripción                                                                                                                  |
| ------------------------ | -------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| id                       | id                   | Identificador único del registro <br> *Unique identifier of the record*                                                      |
| product_id               | fk_producto          | Referencia al producto <br> *Reference to the product*                                                                       |
| presentation_id          | fk_presentacion      | Referencia a la presentación <br> *Reference to the presentation*                                                            |
| sale_price               | precio_venta         | Precio de venta para esa presentación <br> *Sale price for this specific presentation*                                       |
| is_default               | presentacion_default | Indica si es la presentación principal del producto <br> *Indicates whether this is the default presentation of the product* |
| is_active                | estado / activo      | Indica si la presentación del producto está Activa <br> *Indicates whether the product presentation is Active*               |
| created_by               | creado_por           | Usuario que creó el registro <br> *User who created the record*                                                              |
| updated_by               | actualizado_por      | Usuario que actualizó el registro <br> *User who updated the record*                                                         |
| created_at               | fecha_creacion       | Fecha de creación del registro <br> *Date when the record was created*                                                       |
| updated_at               | fecha_actualizacion  | Fecha de actualización del registro <br> *Date when the record was last updated*                                             |

>[!NOTE]
>Es necesario evitar la duplicación de la misma presentación para un producto con el siguiente constraint
>```SQL
>  UNIQUE (product_id, presentation_id)
>```
>También se debe garantizar que el mismo producto no pueda tener más de 1 is_default = true
>```SQL
>  CREATE UNIQUE INDEX unique_default_presentation
>  ON product_presentations (product_id)
>  WHERE is_default = true;
>```
>>El campo *is_default* se debe especificar como tipo boolean, donde 1 indica que es el campo por defecto.

## product_prices | Producto_Precio

**Descripción:** Registra la información del histórico de precios de cada producto. Pero solo se usará como tabla de consulta de históricos, para estadísticas porque el valor del producto como tal se obtiene de la tabla product_presentations.

| Campo (Laravel / Inglés) | Traducción               | Descripción                                                                      |
| ------------------------ | ------------------------ | -------------------------------------------------------------------------------- |
| id                       | id                       | Identificador único del registro <br> *Unique identifier of the record*          |
| product_id               | fk_producto              | Referencia al producto <br> *Reference to the product*                           |
| product_presentation_id  | fk_producto_presentacion | Referencia a product_presentations <br> *Reference to the product_presentations* |
| sale_price               | precio_venta_producto    | Precio de venta del producto <br> *Sale price of the product*                    |
| purchase_reference_price | precio_compra_referencia | Precio de compra de referencia <br> *Reference purchase price*                   |
| start_date               | fecha_inicio             | Fecha de inicio del precio <br> *Start date of the price validity*               |
| end_date                 | fecha_final              | Fecha de finalización del precio <br> *End date of the price validity*           |
| created_by               | creado_por               | Usuario que creó el registro <br> *User who created the record*                  |
| updated_by               | actualizado_por          | Usuario que actualizó el registro <br> *User who updated the record*             |
| created_at               | fecha_creacion           | Fecha de creación del registro <br> *Date when the record was created*           |
| updated_at               | fecha_actualizacion      | Fecha de actualización del registro <br> *Date when the record was last updated* |

>[!NOTE]
>Se debe garantizar la *end_date* (fecha_final) sea igual o superior a la *start_date* (fecha_inicio) así:
>```SQL
>  CHECK (end_date IS NULL OR end_date > start_date)
>```
>En el campo *start_date* se registra un nuevo precio (Se crea al mismo tiempo que la creación del registro)
>En el campo *end_date* se registra la duración del precio (Se actualiza de null a la nueva fecha cuando existe un nuevo precio del mismo producto y es el equivalente a la fecha de inicio de la siguiente creación del registro del precio)

## season | Temporada

**Descripción:** Solo registra el nombre de las temporadas de ventas. <br> *Ejemplo:* Temporada escolar, Comfaboy, ...

| Campo (Laravel / Inglés) | Traducción           | Descripción                                                                      |
| ------------------------ | -------------------- | -------------------------------------------------------------------------------- |
| id                       | id                   | Identificador único de la temporada <br> *Unique identifier of the season*       |
| name                     | nombre_temporada     | Nombre de la temporada <br> *Name of the season*                                 |
| has_global_pricing       | aplica_precio_global | `true`, `false`                                                                  |
| adjustment_type          | tipo_ajuste_global   | `DESCUENTO`, `RECARGO`                                                           |
| adjustment_mode          | modo_ajuste_global   | `PORCENTAJE`, `VALOR`                                                            |
| adjustment_value         | valor_ajuste_global  | Número ≥ 0                                                                       |
| created_by               | creado_por           | Usuario que creó el registro <br> *User who created the record*                  |
| updated_by               | actualizado_por      | Usuario que actualizó el registro <br> *User who updated the record*             |
| created_at               | fecha_creacion       | Fecha de creación del registro <br> *Date when the record was created*           |
| updated_at               | fecha_actualizacion  | Fecha de actualización del registro <br> *Date when the record was last updated* |

>[!NOTE]
>A esta tabla se agregan los campos:
>```
> has_global_pricing (aplica_precio_global)
> adjustment_type (tipo_ajuste_global)
> adjustment_value (valor_ajuste_global)
>```
>Con el fin de asignar datos globales sobre el incremento o descuento de todos los productos por defecto, siempre y cuando en la tabla *season_product_pricing* no se haya especificado algún valor en particular

## season_product_pricing | Precios de productos según temporada

**Descripción:** Define cómo se calcula o reemplaza el precio de un producto (por presentación) dentro de una temporada.

| Campo (Laravel / Inglés) | Traducción               | Justificación                                              | Valores permitidos                             |
| ------------------------ | ------------------------ | ---------------------------------------------------------- | ---------------------------------------------- |
| id                       | id                       | Identificador único del registro.                          | Entero autoincremental                         |
| season_id                | fk_temporada             | Relaciona el precio con una temporada (Escolar, Comfaboy). | Entero (FK válida)                             |
| product_presentation_id  | fk_producto_presentacion | Define a qué presentación del producto aplica el precio.   | Entero (FK válida)                             |
| pricing_type             | tipo_precio              | Define si el precio se reemplaza o se calcula.             | **FIJO**, **AJUSTE**                           |
| override_price           | precio_fijo              | Se usa cuando el precio es manual (ignora el precio base). | Número ≥ 0 (NULL si no aplica)                 |
| adjustment_type          | tipo_ajuste              | Indica si el precio sube o baja.                           | **DESCUENTO**, **RECARGO** (NULL si no aplica) |
| adjustment_mode          | modo_ajuste              | Define cómo se calcula el ajuste.                          | **PORCENTAJE**, **VALOR** (NULL si no aplica)  |
| adjustment_value         | valor_ajuste             | Valor del ajuste (porcentaje o monto).                     | Número ≥ 0 (NULL si no aplica)                 |
| is_active                | estado_activo            | Permite activar o desactivar el registro.                  | **true**, **false**                            |
| created_by               | creado_por               | Usuario que creó el registro.                              | Entero (FK opcional)                           |
| updated_by               | actualizado_por          | Usuario que modificó el registro.                          | Entero (FK opcional)                           |
| created_at               | fecha_creacion           | Fecha de creación del registro.                            | Timestamp                                      |
| updated_at               | fecha_actualizacion      | Fecha de actualización del registro.                       | Timestamp                                      |

>[!NOTE]
>**Caso 1: Precio FIJO**
>```
> pricing_type = FIJO
>```
>Debe cumplir:
>```
> precio_fijo → obligatorio
> tipo_ajuste → NULL
> modo_ajuste → NULL
> valor_ajuste → NULL
>```
>>**Ejemplo de Temporada Escolar:**
>```
> tipo_precio = FIJO
> precio_fijo = 1800
>```
>**Caso 2: AJUSTE**
>```
> pricing_type = AJUSTE
>```
>Debe cumplir:
>```
> precio_fijo → NULL
> tipo_ajuste → obligatorio (DESCUENTO o RECARGO)
> modo_ajuste → obligatorio (PORCENTAJE o VALOR)
> valor_ajuste → obligatorio
>```
>>**Ejemplo de Comfaboy:**
>```
> tipo_precio = AJUSTE
> tipo_ajuste = RECARGO
> modo_ajuste = PORCENTAJE
> valor_ajuste = 5
>```
>**Especificación Importante:**
>El valor del campo *valor_ajuste* (*adjustment_value*) hace referencia al valor que se debe restar, según lo que represente, ya sea 100, 200, 350 pesos, pero no es para guardar un segundo valor del producto
>
>*Regla de prioridad (IMPORTANTÍSIMA)*
> 1. Si existe configuración por producto → usar esa
> 2. Si NO → usar configuración global de la temporada
> 3. Si no hay nada → usar precio base

## pending_purchases | Pendiente_compra

**Descripción:** Guarda las compras pendientes generadas por bajo stock o por solicitud de ampliar el stock

| Campo (Laravel / Inglés) | Traducción          | Descripción                                                                                                                                                  |
|--------------------------|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                       | id                  | Identificador único del pendiente de compra Unique identifier of the pending purchase                                                                        |
| product_id               | fk_producto         | Referencia al producto Reference to the product                                                                                                              |
| supplier_id              | fk_proveedor        | Referencia al proveedor (puede ser nulo) Reference to the supplier (nullable)                                                                                |
| pending_date             | fecha_pendiente     | Fecha desde la cual está pendiente la compra Date since the purchase is pending                                                                              |
| quantity                 | cant_pendiente      | Cantidad que se debe comprar Quantity to be purchased                                                                                                        |
| status                   | estado_pendiente    | Estado del pendiente ('PENDIENTE','EN_PROCESO','COMPRADO','CANCELADO') <br> Status of the pending purchase ('PENDIENTE','EN_PROCESO','COMPRADO','CANCELADO') |
| source                   | origen_pendiente    | Origen del pendiente (stock mínimo o manual) <br> Origin of the pending request (minimum stock or manual)                                                    |
| notes                    | observaciones       | Se especifica el motivo del estado del producto a solicitar ya que es posible generar el pendiente y luego cancelarlo                                        |
| created_at               | fecha_creacion      | Fecha de creación del registro Date when the record was created                                                                                              |
| updated_at               | fecha_actualizacion | Fecha de actualización del registro Date when the record was last updated                                                                                    |

>[!NOTE]
>El campo origen_pend se utiliza para especificar si el pendiente de la compra se originó por bajo stock o sencillamente se decidió solicitar más producto teniendo sufieciente stock
>
>Se deben evitar la duplicidad de la misma solicitud del producto que se encuentre en PENDIENTE o EN PROCESO, según el estado, ya que si se puede duplicar cuando el estado es COMPRADO o CANCELADO
>```SQL
>  CREATE UNIQUE INDEX unique_active_pending
>  ON pending_purchases (product_id)
>  WHERE status IN ('pending','in_progress');
>```
>En el campo *status* solo acepta los siguientes valores:
>```SQL
>  ENUM('PENDIENTE','EN_PROCESO','COMPRADO','CANCELADO')
>```
>En el campo *source* solo acepta los siguientes valores:
>```SQL
>  ENUM('STOCK_MINIMO','MANUAL')
>```

## product_requests | Solicitud_producto

**Descripción:** Hace referencia a la anotación de nuevos productos que no existen en el inventario y que se desea traer.

| Campo (Laravel / Inglés) | Traducción           | Descripción                                                                                                           |
|--------------------------|----------------------|-----------------------------------------------------------------------------------------------------------------------|
| id                       | id                   | Identificador único de la solicitud Unique identifier of the request                                                  |
| product_id               | fk_producto          | Referencia al producto (puede ser nulo) Reference to the product (nullable)                                           |
| supplier_id              | fk_proveedor         | Proveedor asociado (puede ser nulo) Associated supplier (nullable)                                                    |
| product_description      | descripcion_producto | Descripción del producto solicitado Description of the requested product                                              |
| quantity                 | cant_solicitud       | Cantidad solicitada Requested quantity                                                                                |
| status                   | estado_solicitud     | ENUM('PENDIENTE','APROBADO','COMPRADO','RECHAZADO')                                                                   |
| priority                 | prioridad            | ENUM(ALTA, MEDIA, BAJA)                                                                                               |
| notes                    | observaciones        | Se especifica el motivo del estado del producto a solicitar ya que es posible generar el pendiente y luego cancelarlo |
| created_by               | creado_por           | Usuario que creó la solicitud User who created the request                                                            |
| approved_by              | aprobado_por         | Usuario que aprobó la solicitud User who approved the request                                                         |
| created_at               | fecha_creacion       | Fecha de creación Creation date                                                                                       |
| approved_at              | fecha_aprobacion     | Fecha de aprobación Approval date                                                                                     |
| updated_by               | actualizado_por      | Usuario que actualizó User who updated the record                                                                     |
| updated_at               | fecha_actualizacion  | Fecha de actualización Last update date                                                                               |

>[!NOTE]
>Teniendo en cuenta que la primera vez que se genera el registro no se ha creado el producto en la base de datos, una vez sea COMPRADO se debe Actualizar el id del producto, junto con el id del proveedor.

## product_files | Archivos adjuntos del producto
**Descripción:** Guarda los nombres de las imágenes y videos del producto.

| Campo (Laravel / Inglés) | Traducción          | Descripción                                                                |
| ------------------------ | ------------------- | -------------------------------------------------------------------------- |
| id                       | id_archivo          | Identificador único del registro <br> *Unique identifier of the record*    |
| file_name                | nombre_archivo      | Nombre del archivo multimedia <br> *Name of the multimedia file*           |
| file_type                | tipo_archivo_prodiv | Tipo de archivo (imagen o video) <br> *Type of file (image or video)*      |
| product_id               | fk_producto         | Referencia al producto relacionado <br> *Reference to the related product* |

## product_codes | Producto_codigo
**Descripción:** Un mismo tipo de producto puede tener varios códigos de barra y por ende varios códigos manuales, sobretodo marcas blancas. El software mostrará en pantalla las opciones encontradas con el mismo código en caso de repetirse con la de algún otro producto. Ya que varios proveedores manejan su propio sistema de códigos de barra.

| Campo (Laravel / Inglés) | Traducción    | Descripción                                                                                                                                      |
| ------------------------ | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| id                       | id_codigo     | Identificador único del código <br> *Unique identifier of the code*                                                                              |
| barcode                  | codigo_barras | Código de barras del producto (pueden existir varios) <br> *Product barcode (multiple values can exist)*                                         |
| manual_code              | codigo_manual | Últimos 6 caracteres del código de barras (usado como identificación manual) <br> *Last 6 characters of the barcode (used as manual identifier)* |
| product_id               | fk_producto   | Referencia al producto <br> *Reference to the product*                                                                                           |

## Locations | Ubicacion
**Descripción:** Se registra el nombre de las ubicaciones con las que cuenta la empresa para almacenar los productos.  
**Ejemplo:** Bodega 1, Bodega 2, Almacén

| Campo (Laravel / Inglés) | Tu campo original   | Descripción                                                                                                                          |
| ------------------------ | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| id                       | id_ubicacion        | Identificador único de ubicación <br> *Unique identifier of the location*                                                            |
| name                     | nombre_ubicacion    | Nombre del lugar donde se almacena el producto (unique) <br> *Name of the place where the product is stored (unique)*                |
| is_default               | ubicacion_default   | Indica si es la ubicación que cargará por defecto en el formulario <br> *Indicates whether this is the default location in the form* |
| is_active                | status_ubicacion    | Indica si la ubicación está Activa (1) o Inactiva (0) <br> *Indicates whether the location is Active (1) or Inactive (0)*            |
| created_by               | creado_por          | Usuario que creó el registro <br> *User who created the record*                                                                      |
| created_at               | fecha_creacion      | Fecha de creación del registro <br> *Date when the record was created*                                                               |
| updated_by               | actualizado_por     | Usuario que actualizó el registro <br> *User who updated the record*                                                                 |
| updated_at               | fecha_actualizacion | Fecha de actualización del registro <br> *Date when the record was last updated*                                                     |

>[!NOTE]
>Es necesario asegurar que:
>   - name tenga índice único
>   - is_default tenga restricción (solo 1 true)
>```SQL
>  CREATE UNIQUE INDEX unique_default_location
>  ON locations (is_default)
>  WHERE is_default = true;
>```

## Location_snapshots | Snapshot_ubicacion
**Descripción:** Es una caché para almacenar y actualizar en un mismo registro la cantidad existente de un producto en cierta ubicación, va de la mano con la Movimiento_inventario. Se actualiza en cada movimiento. 
**Ejemplo:** 200 Lapices Mirado en Bodega 1, 25 Lapices Mirado en Almacén  

| Campo (Laravel / Inglés) | Tu campo original   | Descripción                                                                                |
| ------------------------ | ------------------- | ------------------------------------------------------------------------------------------ |
| id                       | id_produb           | Identificador único <br> *Unique identifier of the record*                                 |
| product_id               | fk_producto         | Referencia al producto <br> *Reference to the product*                                     |
| location_id              | fk_ubicacion        | Referencia al lugar de ubicación <br> *Reference to the location*                          |
| quantity                 | cant_produb         | Cantidad del producto en esa ubicación <br> *Quantity of the product in that location*     |
| updated_at               | fecha_actualizacion | Fecha de la última actualización del registro <br> *Date when the record was last updated* |

>[!NOTE]
>Se debe evitar duplicadosen los que se repiten llaves foráneas en el mismo registro:
>
>ALTER TABLE location_snapshots
>ADD CONSTRAINT unique_product_location
>UNIQUE (product_id, location_id);

## Departments | Departamento
**Descripción:** Almacena los nombres de los departamentos de Colombia

| Campo (Laravel / Inglés) | Tu campo original | Descripción                                                 |
| ------------------------ | ----------------- | ----------------------------------------------------------- |
| id                       | id_depart         | Identificador del departamento <br> *Department identifier* |
| name                     | nombre_depart     | Nombre del departamento <br> *Department name*              |
| dane_code                | codigo_dane       | Código otorgado por el DANE <br> *DANE code*                |

>[!NOTE]
>Se debe agregar restricción única al nombre:
>```SQL
> CREATE UNIQUE INDEX unique_department_name
> ON departments (name);
>```

## Cities | Ciudad
**Descripción:** Almacena los nombres de los municipios y ciudades que pertenencen a los departamentos de Colombia.

| Campo (Laravel / Inglés) | Tu campo original | Descripción                                                                  |
| ------------------------ | ----------------- | ---------------------------------------------------------------------------- |
| id                       | id_ciudad         | Identificador de la ciudad <br> *City identifier*                            |
| name                     | nombre_ciudad     | Nombre de la ciudad <br> *City name*                                         |
| department_id            | fk_depart         | Referencia al departamento <br> *Reference to the department*                |
| dane_code                | —                 | Código DANE de la ciudad (5 dígitos) <br> *DANE code of the city (5 digits)* |

>[!NOTE]
>Se debe evitar ciudades duplicadas dentro del mismo departamento:
>```SQL
>  CREATE UNIQUE INDEX unique_city_per_department
>  ON cities (name, department_id);
>```

## Suppliers | Proveedor

| Campo (Laravel / Inglés) | Tu campo original      | Descripción                                                                                                                        |
| ------------------------ | ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| id                       | id_proveedor           | Identificador del proveedor <br> *Supplier identifier*                                                                             |
| document_type            | —                      | Tipo de documento (NIT, CC, CE, etc.) <br> *Type of identification document (NIT, CC, CE, etc.)*                                   |
| document_number          | number_documento       | Numero de documento <br> *identification number*                                                                                   |
| business_name            | razon_social_proveedor | Razón social del proveedor <br> *Supplier business name*                                                                           |
| contact_name             | —                      | Nombre de la persona de contacto principal <br> *Primary contact person's name*                                                    |
| phone                    | —                      | Teléfono principal de contacto <br> *Primary contact phone number*                                                                 |
| email                    | email_principal        | Correo electrónico del proveedor <br> *Supplier email address*                                                                     |
| email_secondary          | email_secundario       | Correo electrónico secundario (*Null* si no aplica) <br> *Secondary email address*.                                                |
| address                  | direccion_proveedor    | Dirección del proveedor <br> *Supplier address*                                                                                    |
| city_id                  | fk_ciudad              | Referencia a la ciudad del proveedor <br> *Reference to the supplier's city*                                                       |
| is_active                | status_proveedor       | Indica si el proveedor está habilitado (1) o deshabilitado (0) <br> *Indicates whether the supplier is active (1) or inactive (0)* |
| created_by               | fk_usuario             | Usuario quien creó el registro <br> *User who created the record*                                                                  |
| created_at               | fecha_creacion         | Fecha de creación del registro <br> *Date when the record was created*                                                             |
| updated_by               | fk_usuario             | Usuario quien actualizó el registro <br> *DUser who created the record*                                                            |
| updated_at               | fecha_actualizacion    | Fecha de actualización del registro <br> *Date when the record was last updated*                                                   |

>[!NOTE]
>No permitir que existan dos proveedores con el mismo NIT:
>```SQL
>  CREATE UNIQUE INDEX unique_supplier_tax_id  
>  ON suppliers (tax_id);
>```
>Restricción del campo document_type
>```SQL
>  CHECK (document_type IN ('NIT','CC','CE'))
>```

## Supplier_phones | Telefono_proveedor

**Descripción:** Por lo general un proveedor tiene varios teléfonos y es necesario guardarlos todos

| Campo (Laravel / Inglés) | Tu campo original      | Descripción                                                                                                                                    |
| ------------------------ | ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| id                       | id_tel_proveedor       | Identificador del teléfono <br> *Phone record identifier*                                                                                      |
| phone                    | numero_tel_proveedor   | Número de teléfono <br> *Phone number*                                                                                                         |
| is_whatsapp              | whatsapp_tel_proveedor | Indica si el número está registrado en WhatsApp (1) o no (0) <br> *Indicates whether the number is registered on WhatsApp (1) or not (0)*      |
| is_telegram              | —                      | Indica si el número está registrado en Telegram (1) o no (0) <br> *Indicates whether the number is registered on Telegram (1) or not (0)*      |
| is_signal                | —                      | Indica si el número está registrado en Signal (1) o no (0) <br> *Indicates whether the number is registered on Signal (1) or not (0)*          |
| supplier_id              | fk_proveedor           | Referencia al proveedor <br> *Reference to the supplier*                                                                                       |
| is_active                | status_tel_proveedor   | Indica si el número telefónico está habilitado (1) o deshabilitado (0) <br> *Indicates whether the phone number is active (1) or inactive (0)* |
| created_by               | fk_usuario             | Usuario quien creó el registro <br> *User who created the record*                                                                              |
| created_at               | fecha_creacion         | Fecha de creación del registro <br> *Date when the record was created*                                                                         |
| updated_by               | fk_usuario             | Usuario quien actualizó el registro <br> *DUser who created the record*                                                                        |
| updated_at               | fecha_actualizacion    | Fecha de actualización del registro <br> *Date when the record was last updated*                                                               |

>[!NOTE]
>Evitar el mismo número repetido para el mismo proveedor:
>```SQL
>  CREATE UNIQUE INDEX unique_supplier_phone
>  ON supplier_phones (supplier_id, phone);
>```

## Payment_methods | Metodo_pago

| Campo (Laravel / Inglés) | Tu campo original      | Descripción                                                                                                                           |
| ------------------------ | ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| id                       | id_metodo_pago         | Identificador del método de pago <br> *Payment method identifier*                                                                     |
| name                     | descipcion_metodo_pago | Nombre o descripción del método de pago <br> *Name or description of the payment method*                                              |
| is_active                | status_metodo_pago     | Indica si el método está habilitado (1) o deshabilitado (0) <br> *Indicates whether the payment method is active (1) or inactive (0)* |
| created_by               | fk_usuario             | Usuario quien creó el registro <br> *User who created the record*                                                                     |
| created_at               | fecha_creacion         | Fecha de creación del registro <br> *Date when the record was created*                                                                |
| updated_by               | fk_usuario             | Usuario quien actualizó el registro <br> *DUser who created the record*                                                               |
| updated_at               | fecha_actualizacion    | Fecha de actualización del registro <br> *Date when the record was last updated*                                                      |

>[!NOTE]
>Evitar duplicados del nombre:
>```SQL
>  CREATE UNIQUE INDEX unique_payment_method_name
>  ON payment_methods (name);
>```

## Purchase | Compra_master

**Descripción:** Almacena los datos generales de una compra, pero la relación de productos comprados, se realiza en otra llamada *Compra_detalle*

| Campo (Laravel / Inglés) | Tu campo original            | Descripción                                                                                                          |
| ------------------------ | ---------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| id                       | id_compra_master             | Identificador de la compra <br> *Purchase identifier*                                                                |
| supplier_id              | fk_proveedor                 | Referencia al proveedor <br> *Reference to the supplier*                                                             |
| attachment_path          | nombre_adjunto_compra_master | Ruta o nombre del archivo adjunto (factura) <br> *Path or name of the attached file (invoice)*                       |
| purchase_date            | fecha_compra_master          | Fecha de la compra <br> *Purchase date*                                                                              |
| subtotal                 | —                            | Suma de los valores de los productos antes de descuentos <br> *Sum of product values before discounts*               |
| total_discount           | total_descuento              | Monto total del descuento aplicable <br> *Total discount amount*                                                     |
| total_amount             | total_compra_master          | Total general de la compra <br> *Total purchase amount*                                                              |
| notes                    | observaciones_compra_master  | Observaciones sobre la compra <br> *Purchase notes*                                                                  |
| status                   | estado_compra_master         | Estado de la compra (PENDIENTE, ABONADA, PAGADA, ANULADA) <br> *Purchase status (PENDING, PARTIAL, PAID, CANCELLED)* |
| created_by               | creado_por                   | Usuario que creó el registro <br> *User who created the record*                                                      |
| created_at               | fecha_creacion               | Fecha de creación de la compra <br> *Date when the purchase was created*                                             |
| updated_by               | actualizado_por              | Usuario que actualizó el registro <br> *User who updated the record*                                                 |
| updated_at               | fecha_actualizacion          | Fecha de actualización de la compra <br> *Date when the purchase was last updated*                                   |

>[!NOTE]
>El campo *status (estado_compra_master)* se realizará de forma automática de acuerdo a lo reflejado en los pagos de la tabla abono_compra
>>CASOS:
>```
>  saldo = total → PENDIENTE
>  saldo > 0 → ABONADA
>  saldo = 0 → PAGADA
>```
>Para la opción de anulada, se mostrará en la vista index la opciónde anular factura, junto con las opciones de editar e inactivar. 

## Purchase_details | Compra_detalle

**Descripción:** Relaciona todos los productos comprados que pertenezcan a la *Compra_Master*

| Campo (Laravel / Inglés) | Tu campo original                | Descripción                                                                                                      |
| ------------------------ | -------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| id                       | id_compra_detalle                | Identificador del detalle de compra <br> *Purchase detail identifier*                                            |
| purchase_id              | fk_compra_master                 | Referencia a la compra <br> *Reference to the purchase*                                                          |
| product_presentation_id  | fk_producto_presentacion         | Referencia a la presentación del producto <br> *Reference to the purchased product presentation*                 |
| quantity                 | cant_compra_detalle              | Cantidad de producto comprado <br> *Quantity purchased*                                                          |
| unit_price               | valor_unit_compra_detalle        | Valor unitario del producto <br> *Unit price of the product*                                                     |
| discount_percentage      | xje_desc_compra_detalle          | Porcentaje de descuento ofrecido por el proveedor <br> *Discount percentage offered by the supplier*             |
| discount_amount          | descuento_unit_compra_detalle    | Valor del descuento aplicado <br> *Discount amount applied*                                                      |
| total_amount             | total_compra_detalle             | Total del detalle (cantidad × valor unitario - descuento) <br> *Total amount (quantity × unit price - discount)* |
| sale_price               | valor_venta_compra_detalle       | Precio de venta sugerido del producto <br> *Suggested sale price*                                                |
| expiration_date          | fecha_vencimiento_compra_detalle | Fecha de vencimiento del producto (si aplica) <br> *Product expiration date (if applicable)*                     |

>[!NOTE]
>En el campo *valor_descuento* (*discount_amount*) solo se debe guardar el valor que se debe restar ya sea 200,300,500, pero **NO** es para guardar un segundo valor del mismo producto.
>Indices a crear:
>```SQL
>  CREATE INDEX idx_purchase_detail_purchase
>  ON purchase_details (purchase_id);
>
>  CREATE INDEX idx_purchase_detail_product
>  ON purchase_details (product_presentation_id);
>```

## Purchase_payments | Abono_compra

**Descripción:** Esta almacena los diferentes nombres de los archivos adjuntos que son comprobantes de abonos realizados o pago total. Según esta se puede saber la cantidad de veces que ha abonado al proveedor sobre la misma factura 

| Campo (Laravel / Inglés) | Tu campo original               | Descripción                                                                        |
| ------------------------ | ------------------------------- | ---------------------------------------------------------------------------------- |
| id                       | id_abono_compra                 | Identificador del abono <br> *Payment identifier*                                  |
| purchase_id              | fk_compra_master                | Referencia a la compra <br> *Reference to the purchase*                            |
| payment_method_id        | fk_metodo_pago                  | Referencia al método de pago <br> *Reference to the payment method*                |
| transaction_type         | movimiento_abono_compra         | Tipo de movimiento (ABONO, DEVOLUCION) <br> *Transaction type (PAYMENT, REFUND)*   |
| amount                   | monto_abono_compra              | Valor abonado o pagado <br> *Payment amount*                                       |
| receipt_file             | nombre_comprobante_abono_compra | Nombre del archivo comprobante de pago <br> *Payment receipt file name*            |
| payment_date             | fecha_hora_abono_compra         | Fecha y hora del pago <br> *Payment date and time*                                 |
| notes                    | observaciones_abono_compra      | Observaciones del pago <br> *Payment notes*                                        |
| created_by               | creado_por                      | Usuario que creó el registro <br> *User who created the record*                    |
| created_at               | fecha_creacion                  | Fecha de creación de la compra <br> *Date when the purchase was created*           |
| updated_by               | actualizado_por                 | Usuario que actualizó el registro <br> *User who updated the record*               |
| updated_at               | fecha_actualizacion             | Fecha de actualización de la compra <br> *Date when the purchase was last updated* |

>[!NOTE]
>```SQL
>  CHECK (transaction_type IN ('ABONO','DEVOLUCION'))
>```

## Purchase_returns | Devolucion_compra

**Descripción:** Esta relaciona los productos que se devuelven al proveedor con su respectiva justificación.

| Campo (Laravel / Inglés) | Tu campo original               | Descripción                                                                                                                            |
| ------------------------ | ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| id                       | id_devolucion_compra            | Identificador de la devolución <br> *Purchase return identifier*                                                                       |
| purchase_detail_id       | fk_compra_detalle               | Referencia al detalle de compra <br> *Reference to the purchase detail*                                                                |
| return_date              | fecha_hora_devolucion_compra    | Fecha de la devolución <br> *Return date*                                                                                              |
| quantity                 | cant_devolucion_compra          | Cantidad devuelta del producto <br> *Returned quantity*                                                                                |
| is_processed             | estado_devolucion_compra        | Indica si la devolución fue procesada (*pendiente*) (1) o no (0) <br> *Indicates whether the return has been processed (1) or not (0)* |
| notes                    | observaciones_devolucion_compra | Justificación de la devolución <br> *Reason for the return*                                                                            |
| created_by               | creado_por                      | Usuario que creó el registro <br> *User who created the record*                                                                        |
| created_at               | fecha_creacion                  | Fecha de creación de la compra <br> *Date when the purchase was created*                                                               |
| updated_by               | actualizado_por                 | Usuario que actualizó el registro <br> *User who updated the record*                                                                   |
| updated_at               | fecha_actualizacion             | Fecha de actualización de la compra <br> *Date when the purchase was last updated*                                                     |

>[!NOTE]
>Verificar que la cantidad devuelta no sea inferior a la cantidad comprada
>```SQL
>   CHECK (quantity > 0)
>```
>Y a nivel de lógica
>```SQL
>   SUM(devoluciones) <= cantidad comprada
>```
> Es necesario verificar si la devolución del producto afecta el stock ya que pudo haberse ingresado y luego darse cuenta de alguna falla en el producto.

## Users | Usuario
**Descripción:** Almacena la información de los usuarios del sistema.

| Campo (Laravel / Inglés) | Tu campo original         | Descripción                                                                                                                  |
| ------------------------ | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| id                       | id_usuario_sistema        | Identificador del usuario <br> *User identifier*                                                                             |
| name                     | nombre_usuario_sistema    | Nombre del usuario <br> *User full name*                                                                                     |
| username                 | nickname_usuario_sistema  | Nombre de usuario para acceso <br> *Username for login*                                                                      |
| password                 | password_usuario_sistema  | Contraseña de acceso (encriptada) <br> *Encrypted password*                                                                  |
| phone                    | tel_usuario_sistema       | Teléfono del usuario <br> *User phone number*                                                                                |
| address                  | dir_usuario_sistema       | Dirección del usuario <br> *User address*                                                                                    |
| email                    | email_usuario_sistema     | Correo electrónico del usuario <br> *User email address*                                                                     |
| email_verified_at        | fecha_email_verificado    | Guarda la fecha en la que el usuario verificó el correo, es decir inicialmente va a ser un campo nulo                        |
| remember_token           | token_usuario_sistema     | Token para recordar sesión o recuperación <br> *Token for session persistence or recovery*                                   |
| last_login_at            | ultima_sesion_iniciada    | Fecha de la última sesión iniciada <br> *date of the last session started*                                                   |
| city_id                  | fk_ciudad                 | Referencia a la ciudad del usuario <br> *Reference to the user's city*                                                       |
| is_active                | status_usuario_sistema    | Indica si el usuario está habilitado (1) o deshabilitado (0) <br> *Indicates whether the user is active (1) or inactive (0)* |
| created_at               | fecha_registro_creado     | Fecha de creación del registro. <br> Record creation date                                                                    |
| updated_at               | fecha_registro_actualizado| Fecha de actualización del registro. <br> Record update date                                                                 |

>[!NOTE]
> - Primero es necesario cotejar con los campos que crea laravel de forma automática
> - Campos únicos (OBLIGATORIO):
>```SQL
> UNIQUE (username)
> UNIQUE (email)
>```

## Customers | Cliente
**Descripción:** Almacena clientes tanto corporativos como particulares

| Campo (Laravel / Inglés) | Tu campo original    | Descripción                                                                                                                         |
| ------------------------ | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| id                       | id_cliente           | Identificador del cliente <br> *Customer identifier*                                                                                |
| document_type            | tipo_documento       | Tipo de documento (CC, NIT, CE, etc.) <br> *Type of identification document*                                                        |
| document_number          | cedula_nit_cliente   | Número de identificación del cliente <br> *Customer identification number*                                                          |
| business_name            | razon_social_cliente | Nombre o razón social del cliente <br> *Customer name or business name*                                                             |
| phone                    | tel_cliente          | Teléfono del cliente. Puede ser nulo si es corporativo <br> *Customer phone number. Maybe null whether the costumer is corporative* |
| address                  | direccion_cliente    | Dirección del cliente <br> *Customer address*                                                                                       |
| email                    | email_cliente        | Correo electrónico del cliente <br> *Customer email address*                                                                        |
| is_company               | es_coporativo        | Guarda Verdadero o Falso <br> *It stores True or False, but default is False*                                                       |
| city_id                  | fk_ciudad            | Referencia a la ciudad <br> *Reference to the city*                                                                                 |
| created_by               | creado_por           | Usuario que creó el registro <br> *User who created the record*                                                                     |
| created_at               | fecha_creacion       | Fecha de creación de la compra <br> *Date when the purchase was created*                                                            |
| updated_by               | actualizado_por      | Usuario que actualizó el registro <br> *User who updated the record*                                                                |
| updated_at               | fecha_actualizacion  | Fecha de actualización de la compra <br> *Date when the purchase was last updated*                                                  |

>[!NOTE]
>Restricción en *is_company*
>```SQL
>  is_company BOOLEAN NOT NULL DEFAULT false
>```
>Creación de índice
>```SQL
>  CREATE UNIQUE INDEX unique_customer_document
>  ON customers (document_type, document_number);
>```

## Customer_employees | Empleado_cliente

**Descripción:** Registra los nombres de los empleados que trabajan para los clientes corporativos que solicitan los productos. Pensado en la trazabilidad de las solicitudes en compras a cŕedito.

| Campo (Laravel / Inglés) | Tu campo original       | Descripción                                                                                                          |
| ------------------------ | ----------------------- | -------------------------------------------------------------------------------------------------------------------- |
| id                       | id_empleado_cliente     | Identificador del empleado del cliente <br> *Customer employee identifier*                                           |
| customer_id              | fk_cliente              | Referencia al cliente corporativo <br> *Reference to the customer (company)*                                         |
| document_type            | tipo_documento_empleado | Tipo de Documento del empleado <br> *Employee document type*                                                         |
| document_number          | cedula_empleado_cliente | Documento del empleado <br> *Employee identification number*                                                         |
| name                     | nombre_empleado_cliente | Nombre del empleado <br> *Employee name*                                                                             |
| job_title                | cargo_empleado          | Cargo en la empresa <br> *Job title*                                                                                 |
| phone                    | tel_empleado_cliente    | Teléfono del empleado <br> *Employee phone number*                                                                   |
| is_default               | valor_predeterminado    | Indica si es el contacto principal del cliente <br> *Indicates whether this is the default contact for the customer* |
| created_by               | creado_por              | Usuario que creó el registro <br> *User who created the record*                                                      |
| created_at               | fecha_creacion          | Fecha de creación de la compra <br> *Date when the purchase was created*                                             |
| updated_by               | actualizado_por         | Usuario que actualizó el registro <br> *User who updated the record*                                                 |
| updated_at               | fecha_actualizacion     | Fecha de actualización de la compra <br> *Date when the purchase was last updated*                                   |
>[!NOTE]
>  Solo un contacto principal por cliente
>```SQL
>  CREATE UNIQUE INDEX unique_default_employee_per_customer
>  ON customer_employees (customer_id)
>  WHERE is_default = true;
>```
>
>Evitar la duplicación del mismo empleado
>```SQL
>  CREATE UNIQUE INDEX unique_employee_per_customer
>  ON customer_employees (customer_id, document_number);
>```
>Tipo de dato
>```SQL
>  is_default BOOLEAN NOT NULL DEFAULT false
>```

## expenses (gastos)

**Descripción:** Representa dinero que sale de caja por operaciones del negocio

| Campo (Laravel / Inglés) | Nombre original (Español) | Objetivo del campo                   | Valores                |
| ------------------------ | ------------------------- | ------------------------------------ | ---------------------- |
| id                       | id_gasto                  | Identificador del gasto              | SERIAL                 |
| cash_register_id         | fk_caja                   | Caja desde donde se realiza el gasto | FK → cash_registers.id |
| expense_category_id      | fk_categoria_gasto        | Clasificación del gasto              | FK                     |
| amount                   | monto_gasto               | Valor del gasto                      | NUMERIC > 0            |
| description              | descripcion               | Motivo del gasto                     | TEXT                   |
| expense_date             | fecha_gasto               | Fecha del gasto                      | TIMESTAMP              |
| created_by               | creado_por                | Usuario que registra                 | FK → users.id          |
| created_at               | fecha_creacion            | Fecha de creación                    | TIMESTAMP              |

>[!NOTE]
>índices recomendados:
>```SQL
>  INDEX (cash_register_id)
>  INDEX (expense_category_id)
>  INDEX (expense_date)
>```

## expense_categories (categorias_gasto)
**Descripción:** Para organización y reportes

| Campo      | Nombre original    | Objetivo         | Valores   |
| ---------- | ------------------ | ---------------- | --------- |
| id         | id_categoria_gasto | Identificador    | SERIAL    |
| name       | nombre_categoria   | Nombre del gasto | VARCHAR   |
| is_active  | estado             | Activo o no      | BOOLEAN   |
| created_at | fecha_creacion     | Fecha            | TIMESTAMP |

>[!NOTE]
>*Ejemplos:*
> - Energía eléctrica
> - Agua
> - Internet
> - Gas

## other_income (otros_ingresos)

**Descripción:** Representa dinero que entra a caja pero NO viene de ventas

| Campo (Laravel / Inglés) | Nombre original (Español) | Objetivo del campo         | Valores     |
| ------------------------ | ------------------------- | -------------------------- | ----------- |
| id                       | id_ingreso                | Identificador              | SERIAL      |
| cash_register_id         | fk_caja                   | Caja donde entra el dinero | FK          |
| income_category_id       | fk_categoria_ingreso      | Tipo de ingreso            | FK          |
| amount                   | monto_ingreso             | Valor recibido             | NUMERIC > 0 |
| description              | descripcion               | Motivo                     | TEXT        |
| income_date              | fecha_ingreso             | Fecha                      | TIMESTAMP   |
| created_by               | creado_por                | Usuario                    | FK          |
| created_at               | fecha_creacion            | Fecha                      | TIMESTAMP   |

>[!NOTE]
>*índices recomendados:*
>```SQL
>   INDEX (cash_register_id)
>   INDEX (income_category_id)
>   INDEX (income_date)
>```

## income_categories (categorias_ingreso)

| Campo      | Nombre original      | Objetivo           | Valores   |
| ---------- | -------------------- | ------------------ | --------- |
| id         | id_categoria_ingreso | Identificador      | SERIAL    |
| name       | nombre_categoria     | Nombre del ingreso | VARCHAR   |
| is_active  | estado               | Activo             | BOOLEAN   |
| created_at | fecha_creacion       | Fecha              | TIMESTAMP |

## Sales | Venta_master

**Descripción:** Al igual que la *Compra_master*, almacena los datos generales de la Venta

| Campo (Laravel / Inglés) | Tu campo original   | Descripción                                                                                                     |
| ------------------------ | ------------------- | --------------------------------------------------------------------------------------------------------------- |
| id                       | id_venta_master     | Identificador de la venta <br> *Sale identifier*                                                                |
| sale_number              | numero_venta_master | Número consecutivo de la venta <br> *Sequential sale number*                                                    |
| electronic_invoice_number| numero_fact_elect   | Número de la facturación electrónica. Permite valores null                                                      |
| customer_id              | fk_cliente          | Referencia al cliente <br> *Reference to the customer*                                                          |
| customer_employee_id     | fk_empleado_cliente | Referencia al empleado del cliente corporativo que realizó el pago.                                             |
| sale_date                | fecha_hora          | Fecha de la venta <br> *Sale date*                                                                              |
| subtotal                 | subtotal            | Suma de los productos antes de descuentos <br> *Sum of items before discounts*                                  |
| total_discount           | total_descuento     | Total de descuentos aplicados <br> *Total discount amount*                                                      |
| total_amount             | total_venta         | Total final de la venta <br> *Final sale amount*                                                                |
| balance_due              | saldo_pendiente     | Saldo pendiente por pagar <br> *Outstanding balance*                                                            |
| notes                    | observaciones       | Observaciones de la venta <br> *Sale notes*                                                                     |
| status                   | estado_factura      | Estado de la venta (PENDIENTE, ABONADA, PAGADA, ANULADA) <br> *Sale status (PENDING, PARTIAL, PAID, CANCELLED)* |
| created_by               | creado_por          | Usuario que creó el registro <br> *User who created the record*                                                 |
| created_at               | fecha_creacion      | Fecha de creación <br> *Creation date*                                                                          |
| updated_by               | actualizado_por     | Usuario que actualizó <br> *User who updated the record*                                                        |
| updated_at               | fecha_actualizacion | Fecha de actualización <br> *Last update date*                                                                  |

>[!NOTE]
>1. sale_number debe ser único:
>```SQL
>  UNIQUE (sale_number)
>```
>2. El *estado* (status), cambia automáticamente de acuerdo a los abonos
>```SQL
>   CHECK (status IN ('PENDIENTE','ABONADA','PAGADA','ANULADA'))
>```
>3. Índices recomendados (OPTIMIZACIÓN)
> a. Índices básicos
>```SQL
>  CREATE UNIQUE INDEX idx_sales_sale_number
>  ON sales (sale_number);
>```
> b. Índices de consulta frecuente 
>```SQL
>  CREATE INDEX idx_sales_customer
>  ON sales (customer_id);
>
>  CREATE INDEX idx_sales_date
>  ON sales (sale_date);
>
>  CREATE INDEX idx_sales_status
>  ON sales (status);
>```
> c. Índice compuesto (MUY útil en dashboards)
>```SQL
>  CREATE INDEX idx_sales_customer_date
>  ON sales (customer_id, sale_date);
>```
>     Esto optimiza:
>        - Historial de ventas por cliente
>        - Reportes tipo:
>              “ventas de cliente X en rango de fechas”
>  d. Índice para cartera (muy importante)
>```SQL
>  CREATE INDEX idx_sales_balance_due
>  ON sales (balance_due)
>  WHERE balance_due > 0;
>```
>     Esto acelera:
>        Consultas de cartera
>        Ventas pendientes
>
>El campo customer_employee_id, debe permitir valores nulos, debido a que no todos los clientes tienen empleados, y la mayoría son personas naturales
>```SQL
>  customer_employee_id INTEGER NULL
>```
>Foreign Key con valores null. Porque si se elimina el empleado no se pierde la venta, y solo se pierde el contacto asociado
>```SQL
>  FOREIGN KEY (customer_employee_id)
>  REFERENCES customer_employees(id)
>  ON DELETE SET NULL;
>```

## Sale_details | Venta_detalle

**Descripción:** Se relaciona el detalle de cada producto vendido al cliente, la razón por la cual se relaciona el usuario en esta se debe a las ventas a *crédito* que se pueden realizar a un cliente en diferentes fechas, y por lo tanto, pudo venderse el producto por empleados diferentes.

| Campo (Laravel / Inglés) | Tu campo original        | Descripción                                                                                              |
| ------------------------ | ------------------------ | -------------------------------------------------------------------------------------------------------- |
| id                       | id_venta_detalle         | Identificador del detalle de venta <br> *Sale detail identifier*                                         |
| sale_id                  | fk_venta_master          | Referencia a la venta <br> *Reference to the sale*                                                       |
| product_presentation_id  | fk_producto_presentation | Referencia a la presentación del producto <br> *Reference to the product presentation*                   |
| quantity                 | cant_venta_detalle       | Cantidad vendida <br> *Quantity sold*                                                                    |
| unit_price               | valor_unit_venta_detalle | Precio unitario de venta <br> *Unit sale price*                                                          |
| discount_percentage      | xje_descuento_producto   | Porcentaje de descuento del v/unit del producto                                                          |
| discount_amount          | valor_descuento_producto | Descuento aplicado al producto <br> *Discount amount applied to the product*                             |
| total_amount             | total_venta_detalle      | Total del detalle (cantidad × precio_unit) <br> *Total amount (quantity × unit price)*                   |
| created_by               | creado_por               | Usuario que creó el registro <br> *User who created the record*                                          |
| created_at               | fecha_creacion           | Fecha de creación <br> *Creation date*                                                                   |
| updated_by               | actualizado_por          | Usuario que actualizó <br> *User who updated the record*                                                 |
| updated_at               | fecha_actualizacion      | Fecha de actualización <br> *Last update date*                                                           |

>[!Note]
>Es necesario garantizar los campos que deben ser mayor a 0
>```SQL
>   CHECK (quantity > 0)
>   CHECK (unit_price >= 0)
>   CHECK (discount_amount >= 0)
>   CHECK (total_amount >= 0)
>```
>**INDICES**
>a. Índice por venta
>```SQL
>   CREATE INDEX idx_sale_details_sale
>   ON sale_details (sale_id);
>```
>  Objetivo:
>    - Cargar factura
>    - Mostrar detalle de venta
>
>b. Índice por producto
>```SQL
>   CREATE INDEX idx_sale_details_product
>   ON sale_details (product_presentation_id);
>```
>  Objetivo:
>    - Reportes
>    - Estadísticas
>    - Kardex
>c. Índice compuesto (muy potente)
>```SQL
>   CREATE INDEX idx_sale_details_sale_product
>   ON sale_details (sale_id, product_presentation_id);
>```
>  Optimización:
>    - Validaciones
>    - Agrupaciones por producto dentro de una venta
>d. Índice para auditoría por usuario
>```SQL
>   CREATE INDEX idx_sale_details_created_by
>   ON sale_details (created_by);
>```

## Sale_returns | Devolucion_venta

**Descripción:** Esta relaciona los productos que se devuelven por parte del cliente con su respectiva justificación.

| Campo (Laravel / Inglés) | Tu campo original              | Descripción                                                                                                                             |
| ------------------------ | ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| id                       | id_devolucion_venta            | Identificador de la devolución <br> *Sale return identifier*                                                                            |
| sale_detail_id           | fk_venta_detalle               | Referencia al detalle de la venta <br> *Reference to the sale detail*                                                                   |
| returned_at              | fecha_hora_devolucion_venta    | Fecha de la devolución <br> *Return date*                                                                                               |
| quantity                 | cant_devolucion_venta          | Cantidad devuelta del producto <br> *Returned quantity*                                                                                 |
| is_money_refund          | devolucion_dinero              | Indica si la devolución incluye reembolso de dinero (1) o no (0). *Indicates whether the return includes a money refund (1) or not (0)* |
| notes                    | observaciones_devolucion_venta | Justificación de la devolución <br> *Reason for the return*                                                                             |
| created_by               | creado_por                     | Usuario que creó el registro <br> *User who created the record*                                                                         |
| created_at               | fecha_creacion                 | Fecha de creación <br> *Creation date*                                                                                                  |
| updated_by               | actualizado_por                | Usuario que actualizó <br> *User who updated the record*                                                                                |
| updated_at               | fecha_actualizacion            | Fecha de actualización <br> *Last update date*                                                                                          |

>[!NOTE]
>Regla obligatoria a nivel lógico:
>```
>   SUM(quantity devuelta) <= quantity vendida
>```
>
>En caso de devolución del dinero se debe involucrar la tabla abono ventas.
>
>Relación del inventario: Entrada de inventario (si aplica) y Movimiento tipo: DC (Devolución Cliente)
>
>**Indices**
>- *Índice principal*
>```SQL
>   CREATE INDEX idx_sale_returns_sale_detail
>   ON sale_returns (sale_detail_id);
>```
>  Objetivo:
>   - Consultar devoluciones por producto vendido
>   - Auditoría
>- *Índice por fecha*
>```SQL
>   CREATE INDEX idx_sale_returns_date
>   ON sale_returns (return_date);
>```
>  Objetivo:
>   - Reportes
>   - Filtrar devoluciones por rango de fechas
>
> *Índice por usuario*
>```SQL
>   CREATE INDEX idx_sale_returns_created_by
>   ON sale_returns (created_by);
>```
>  Objetivo:
>   - Auditoría por usuario
>
> Validaciones recomendadas
>```SQL
>  CHECK (quantity >= 0)
>```
>
> Integridad lógica
>``` 
> quantity_devuelta > 0
> quantity_devuelta <= cantidad_original
>```

## sale_payments | Abono_venta
**Descripción:** Esta almacena los diferentes nombres de los archivos adjuntos que son comprobantes de abonos realizados o pago total. Según esta se puede saber la cantidad de veces que ha abonado un cliente a la misma factura. 

| Campo (Laravel / Inglés) | Nombre original (Español) | Objetivo del campo               | Valores                 |
| ------------------------ | ------------------------- | -------------------------------- | ----------------------- |
| id                       | id_abono_venta            | Identificador del pago           | SERIAL                  |
| sale_id                  | fk_venta_master           | Relación con la venta            | FK → sales.id           |
| payment_method_id        | fk_metodo_pago            | Método de pago utilizado         | FK → payment_methods.id |
| transaction_type         | tipo_movimiento           | Tipo de operación                | ENUM (Pago, Devolución) |
| received_amount          | valor_recibido            | Dinero recibido del cliente      | NUMERIC > 0             |
| applied_amount           | valor_aplicado            | Valor aplicado a la deuda        | NUMERIC ≥ 0             |
| change_amount            | valor_cambio              | Dinero devuelto al cliente       | NUMERIC ≥ 0             |
| payment_date             | fecha_hora_abono_venta    | Fecha y hora del pago            | TIMESTAMP               |
| receipt_file             | comprobante_abono_venta   | Nombre comprobante (.jpg o .pdf) | VARCHAR NULL            |
| notes                    | observaciones_abono_venta | Observaciones                    | TEXT                    |
| created_by               | creado_por                | Usuario que registra             | FK → users.id           |
| created_at               | fecha_creacion            | Fecha de creación                | TIMESTAMP               |
| updated_at               | fecha_actualizacion       | Fecha de actualización           | TIMESTAMP               |

>[!NOTE]
>Es necesario aclarar que esta tabla interpreta el ingreso del dinero de dos maneras, la primera el pago por parte del cliente sin importar el medio, y la segunda la devolución de un producto por parte del cliente.<br> 
> Valores de *transaction_type* (tipo_movimiento):
>  | Valor   | Significado          |
>  | ------- | -------------------- |
>  | PAYMENT | Pago normal          |
>  | REFUND  | Devolución de dinero |
>
>Validaciones a implementar:
>```SQL
>   CHECK (received_amount > 0)
>   CHECK (applied_amount >= 0)
>   CHECK (change_amount >= 0)
>```
>**SOLO afecta caja** si *payment_method = EFECTIVO*
>
>**Indices**
>```SQL
>   CREATE INDEX idx_sale_payments_sale
>   ON sale_payments (sale_id);
>```
>```SQL
>   CREATE INDEX idx_sale_payments_method
>   ON sale_payments (payment_method_id);
>```
>```SQL
>   CREATE INDEX idx_sale_payments_date
>   ON sale_payments (payment_date);
>```
>```SQL
>   CREATE INDEX idx_sale_payments_user
>   ON sale_payments (created_by);
>```

## cash_registers (cajas / turnos de caja)

**Descripcion:** Representa la apertura de caja de un usuario (no necesariamente diario)

| Campo (Laravel / Inglés) | Nombre original (Español) | Objetivo del campo                        | Valores                 |
| ------------------------ | ------------------------- | ----------------------------------------- | ----------------------- |
| id                       | id_caja                   | Identificador único                       | SERIAL / AUTO INCREMENT |
| user_id                  | fk_usuario                | Usuario que abre la caja                  | FK → users.id           |
| opening_amount           | monto_apertura            | Dinero inicial con el que se abre la caja | NUMERIC ≥ 0             |
| opened_at                | fecha_apertura            | Fecha y hora de apertura                  | TIMESTAMP               |
| closed_at                | fecha_cierre              | Fecha y hora de cierre                    | TIMESTAMP NULL          |
| status                   | estado_caja               | Estado actual de la caja                  | ENUM('OPEN','CLOSED')   |
| created_at               | fecha_creacion            | Fecha de creación del registro            | TIMESTAMP               |

>[!NOTE]
> *Regla clave:* Solo una caja abierta por usuario:
>```SQL
>  UNIQUE (user_id) WHERE status = 'OPEN'
>```

## cash_movements (movimientos de caja)

**Descripcion:** Aquí se registra TODO el dinero (es la tabla más importante)

| Campo (Laravel / Inglés) | Nombre original (Español) | Objetivo del campo                         | Valores                |
| ------------------------ | ------------------------- | ------------------------------------------ | ---------------------- |
| id                       | id_movimiento_caja        | Identificador único                        | SERIAL                 |
| cash_register_id         | fk_caja                   | Relación con la caja abierta               | FK → cash_registers.id |
| type                     | tipo_movimiento           | Tipo de movimiento de dinero               | ENUM (ver abajo)       |
| amount                   | monto                     | Valor del movimiento                       | NUMERIC > 0            |
| reference_id             | id_referencia             | ID del registro origen (venta, pago, etc.) | INTEGER                |
| reference_type           | tipo_referencia           | Tabla origen del movimiento                | VARCHAR                |
| description              | descripcion               | Motivo o detalle del movimiento            | TEXT                   |
| created_at               | fecha_creacion            | Fecha del movimiento                       | TIMESTAMP              |

>[!NOTE]
>No puede existir movimiento sin caja abierta.
>*Valores del campo type:*
>  | Valor        | Significado                |
>  | ------------ | -------------------------- |
>  | SALE_CASH    | Venta pagada en efectivo   |
>  | PAYMENT_CASH | Abono en efectivo          |
>  | REFUND_CASH  | Devolución de dinero       |
>  | EXPENSE      | Gasto de caja              |
>  | INCOME       | Ingreso manual             |
>  | ADJUSTMENT   | Ajuste (faltante/sobrante) |

## cash_closings (cierres de caja)

**Descripcion:** Resume el cierre de una caja

| Campo (Laravel / Inglés) | Nombre original (Español) | Objetivo del campo               | Valores                      |
| ------------------------ | ------------------------- | -------------------------------- | ---------------------------- |
| id                       | id_cierre_caja            | Identificador del cierre         | SERIAL                       |
| cash_register_id         | fk_caja                   | Caja que se está cerrando        | FK → cash_registers.id       |
| expected_amount          | monto_esperado            | Dinero esperado según sistema    | NUMERIC ≥ 0                  |
| actual_amount            | monto_real                | Dinero contado físicamente       | NUMERIC ≥ 0                  |
| difference               | diferencia                | Diferencia entre esperado y real | NUMERIC (puede ser negativo) |
| notes                    | observaciones             | Justificación del cierre         | TEXT                         |
| closed_by                | cerrado_por               | Usuario que realiza el cierre    | FK → users.id                |
| created_at               | fecha_creacion            | Fecha del cierre                 | TIMESTAMP                    |

>[!NOTE]
>Lógica de las cajas:<br>
> **Ingresos (entra dinero):**
>  - SALE_CASH (venta en efectivo)
>  - PAYMENT_CASH (abono)
>  - INCOME (ingreso manual)
>
> **Egresos (sale dinero):**
>  - REFUND_CASH (devolución)
>  - EXPENSE (gasto)
>
>Cálculo de diferencia: difference = actual_amount - expected_amount
>
>**Falta hacer el mapa de su integración con otras tablas**

## inventory_movements | Movimiento_inventario
**Descripción:** Se realizarán los inventarios FIFO Y PONDERADO

| Campo (Laravel / Inglés) | Nombre original (Español) |                                                     Objetivo del campo                                                     |      Valores       |
|:------------------------:|:-------------------------:|:--------------------------------------------------------------------------------------------------------------------------:|--------------------|
| id                       | id_inventario             | Identificador del movimiento                                                                                               | SERIAL             |
| product_id               | fk_producto               | Producto afectado                                                                                                          | FK → products.id   |
| movement_type            | tipo_inventario           | Tipo de movimiento                                                                                                         | ENUM (ver abajo)   |
| quantity                 | cant_inventario           | Cantidad del movimiento                                                                                                    | NUMERIC > 0        |
| unit_cost                | valor_unit_inventario     | Costo unitario (solo entradas), para salidas se utilia NULL, ya que se calcula de acuerdo al tipo de inv                   | NUMERIC ≥ 0 / NULL |
| movement_date            | fecha_hora_inventario     | Fecha del movimiento                                                                                                       | TIMESTAMP          |
| purchase_detail_id       | fk_compra_detalle         | Referencia detalle compra                                                                                                  | FK NULL            |
| sale_detail_id           | fk_venta_detalle          | Referencia detalle venta                                                                                                   | FK NULL            |
| location_id              | fk_ubicacion              | Referencia a la Ubicación                                                                                                  | FK                 |
| movement_group_id        | id_grupo_movimiento       | Se usa para agrupar movimientos que pertenecen a una misma operación   (compra distribuida, venta, traslado, ajuste, etc.) | INTEGER NULL       |
| notes                    | observaciones             | En caso de haber devoluciones, ajustes, traslados, se debe especificar la razón por la que se dió este movimiento          | TEXT               |
| created_at               | fecha_creacion            | Fecha de creación                                                                                                          | TIMESTAMP          |

>[!NOTE]
>**Valores de movement_type (tipo_inventario)**
>| Código | Significado          |
>| ------ | -------------------- |
>| IN     | Inventario inicial   |
>| C      | Compra               |
>| V      | Venta                |
>| DC     | Devolución cliente   |
>| DP     | Devolución proveedor |
>| AP     | Ajuste positivo      |
>| AN     | Ajuste negativo      |
>
>No se relaciona la llave foránea del usuario ya que es una que se alimenta automáticamente de otras tablas que estaría diligenciando el usuario final, sin embargo es el corazón del software.
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
>
>*INDICES*
>Producto:
>```SQL
>   CREATE INDEX idx_inventory_product
>   ON inventory_movements (product_id);
>```
>
>Ubicación:
>```SQL
>   CREATE INDEX idx_inventory_location
>   ON inventory_movements (location_id);
>```
>Fecha:
>```SQL
>   CREATE INDEX idx_inventory_date
>   ON inventory_movements (movement_date);
>```
>Tipo:
>```SQL
>   CREATE INDEX idx_inventory_type
>   ON inventory_movements (movement_type);
>```
>Relaciones:
>```SQL
>   CREATE INDEX idx_inventory_sale
>   ON inventory_movements (sale_detail_id);
>```
>```SQL
>   CREATE INDEX idx_inventory_purchase
>   ON inventory_movements (purchase_detail_id);
>```

## inventory_layers | Inventario_capas
**Descripción:** Tiene como objetivo controlar las salidas de cada capa, ya que el costo puede variar con el tiempo, y es necesaria para determinar el valor real del inventario de cada producto.

| Campo (Laravel / Inglés) | Nombre original (Español) |                                       Objetivo del campo                                       | Valores                     |
|--------------------------|---------------------------|:----------------------------------------------------------------------------------------------:|-----------------------------|
| id                       | id_capa                   | Identificador de la capa                                                                       | SERIAL                      |
| product_id               | fk_producto               | Llave foránea del producto                                                                     | FK → products.id            |
| inventory_movement_id    | fk_movimiento_inventario  | Llave foránea del Movimiento_inventario                                                        | FK → inventory_movements.id |
| initial_quantity         | cant_inicial              | Total de productos ingresados al momento de la entrada ya sea Inventario Inicial o Compras     | NUMERIC > 0                 |
| remaining_quantity       | cant_restante             | Inicia con el mismo valor que cant_inicial y se irá restando (actualizando) con cada salida    | NUMERIC ≥ 0                 |
| unit_cost                | costo_unitario            | Costo unitario de la capa de la compra o inventario inicial                                    | NUMERIC ≥ 0                 |
| layer_date               | fecha_capa                | Fecha de creación de la capa                                                                   | TIMESTAMP                   |
| status                   | estado_capa               | Contendrá dos valores A=Activa o C=Cerrada. solo se cerrará cuando cant_restante sea igual a 0 | ENUM('ACTIVE','CLOSED')     |
| created_at               | fecha_creacion            | Fecha de creación                                                                              | TIMESTAMP                   |

>[!NOTE]
>**Reglas importantes:**
>*Entradas que crean la capa:* 
>| Tipo | Acción    |
>| ---- | --------- |
>| C    | crea capa |
>| IN   | crea capa |
>| DC   | crea capa |
>
>*Entradas que actualizan la capa:* 
>| Tipo | Acción        |
>| ---- | ------------- |
>| V    | consume capas |
>| DP   | consume capas |
>| AN   | consume capas |
>
>**Índices (MUY IMPORTANTES para FIFO)**
>*Producto*
>```SQL
>  CREATE INDEX idx_layers_product
>  ON inventory_layers (product_id);
>```
>
>*Estado + fecha (clave para FIFO)*
>```SQL
>  CREATE INDEX idx_layers_fifo
>  ON inventory_layers (product_id, status, layer_date);
>```
>Esto permite:
>```SQL
>  ORDER BY layer_date ASC
>```

## Inventario_salida_detalle

**Descripción:** Registra el detalle del consumo de inventario por capas para cada venta, permitiendo identificar el costo real de los productos vendidos según el método de costeo (FIFO, o Ponderado).

| Campo (Laravel / Inglés) | Nombre original (Español) | Objetivo del campo                                     | Valores                  |
|--------------------------|---------------------------|--------------------------------------------------------|--------------------------|
| id                       | id_salida_detalle         | Identificador                                          | SERIAL                   |
| sale_detail_id           | fk_venta_detalle          | Llave foránea Venta_detalle                            | FK → sale_details.id     |
| inventory_layer_id       | fk_capa                   | Llave foránea inventario_capas                         | FK → inventory_layers.id |
| product_id               | fk_producto               | Llave foránea de la producto (para agilizar consultas) | FK → products.id         |
| quantity                 | cantidad_salida           | Cantidad vendida tomada de la capa                     | NUMERIC > 0              |
| unit_cost                | costo_unitario            | Costo unitario de la capa                              | NUMERIC ≥ 0              |
| total_cost               | subtotal_costo            | Costo total (cantidad_salida x costo_unitario)         | NUMERIC ≥ 0              |
| created_at               | fecha_registro            | Fecha de registro                                      | TIMESTAMP                |

>[!NOTE]
>**Reglas críticas:**
>*Integridad matemática*
>```SQL
>  CHECK (quantity > 0)
>  CHECK (unit_cost >= 0)
>  CHECK (total_cost = quantity * unit_cost)
>```
>
>**Relación con capas:**
>*Debe cumplirse:*
>```
>   SUM(quantity usada en capas) = cantidad vendida
>```
>
>**NO SE PUEDE consumir más de lo disponible:**
>```
>   quantity <= remaining_quantity (en la capa)
>```
>
>**¿Para qué sirve realmente? (nivel negocio)**
>1. Calcular costo de venta (COGS)
>```
>   costo_total_venta = SUM(total_cost)
>```
>
>2. Calcular utilidad
>```
>   utilidad = venta - costo
>```
>
>3. Auditoría
>Se puede conocer:
> - ¿de qué compra salió este producto?
> - ¿cuánto costó realmente?
> - ¿qué capas se consumieron?
>
>4. Kardex real
>Esto alimenta:
> - FIFO
> - reportes contables
> - Trazabilidad
>
>**Índices recomendados:**
>```SQL
>CREATE INDEX idx_out_sale_detail
>ON inventory_out_details (sale_detail_id);
>```
>
>```SQL
>CREATE INDEX idx_out_layer
>ON inventory_out_details (inventory_layer_id);
>```
>
>```SQL
>CREATE INDEX idx_out_product
>ON inventory_out_details (product_id);
>```

## Kardex_fifo | Kardex_fifo

**Descripción:** Mantiene actualizado el inventario FIFO. Mantiene el histórico acumulado del inventario. Debido a que se manejan ubicaciones, se tendrán registro donde se relacione el total de productos por ubicación.

*Ejemplo:*
 - Producto A - Bodega 1
 - Producto A - Bodega 2

| Campo (Laravel / Inglés) | Tu campo original | Descripción                                                                                   |
| ------------------------ | ----------------- | --------------------------------------------------------------------------------------------- |
| id                       | id_kardex_fifo    | Identificador del registro del kardex <br> *Kardex record identifier*                         |
| inventory_movement_id    | fk_inventario     | Referencia al id del movimiento de inventario <br> *Reference to the inventory movement*      |
| product_id               | fk_producto       | Referencia al producto para agilizar consultas                                                |
| location_id              | fk_ubicacion      | Referencia a la ubicación para agilizar consultas                                             |
| quantity_in              | cant_entrada      | Cantidad que ingresa al inventario <br> *Incoming quantity*                                   |
| quantity_out             | cant_salida       | Cantidad que sale del inventario <br> *Outgoing quantity*                                     |
| balance_quantity         | cant_saldo        | Cantidad restante después del movimiento <br> *Remaining quantity balance*                    |
| balance_value            | valor_saldo       | Valor total del inventario después del movimiento <br> *Inventory total value after movement* |
| movement_date            | fecha_movimiento  | Fecha del movimiento <br> *Movement date*                                                     |

>[!NOTE]
>*Diferencia con otras tablas*
>| Tabla                 | Función                      |
>| --------------------- | ---------------------------- |
>| inventory_movements   | eventos (qué pasó)           |
>| inventory_layers      | costo por capas              |
>| inventory_out_details | consumo exacto               |
>| kardex_fifo           | estado acumulado paso a paso |
>
>*Observaciones importantes (arquitectura)*
>1. Esta tabla es DERIVADA
>Todo lo que tiene se puede calcular desde:
>```
>  inventory_movements
>  inventory_layers
>```
>2. Entonces… ¿por qué existe?
>Por rendimiento y reportes:
> - Reportes rápidos
> - Historial claro
> - Evitar cálculos complejos
>
>*Índices recomendados*
>```SQL
>CREATE INDEX idx_kardex_movement
>ON kardex_fifo (inventory_movement_id);
>```
>```SQL
>CREATE INDEX idx_kardex_date
>ON kardex_fifo (movement_date);
>```

## Kardex_ponderado | Kardex Promedio Ponderado
**Descripción:** Mantiene actualizado el inventario PONDERADO por cada una de las ubicaciones

| Campo (Laravel / Inglés) | Tu campo original   | Descripción                                                                       |
| ------------------------ | ------------------- | --------------------------------------------------------------------------------- |
| id                       | id_kardex_ponderado | Identificador del registro <br> *Kardex weighted record identifier*               |
| inventory_movement_id    | fk_inventario       | Referencia al movimiento de inventario <br> *Reference to the inventory movement* |
| product_id               | fk_producto         | Referencia al producto <br> *Reference to the product table*                      |
| location_id              | fk_ubicacion        | Referencia a la ubicación <br> *Reference to the location table*                  |
| quantity_in              | cant_entrada        | Cantidad que ingresa <br> *Incoming quantity*                                     |
| quantity_out             | cant_salida         | Cantidad que sale <br> *Outgoing quantity*                                        |
| balance_quantity         | cant_saldo          | Cantidad restante después del movimiento <br> *Remaining quantity balance*        |
| balance_value            | valor_saldo         | Valor total del inventario <br> *Total inventory value*                           |
| movement_date            | fecha_movimiento    | Fecha del movimiento <br> *Movement date*                                         |

>[!NOTE]
>1. Diferencia con FIFO
>
>| Método    | Cómo calcula costo       |
>| --------- | ------------------------ |
>| FIFO      | capas (inventory_layers) |
>| Ponderado | promedio acumulado       |
>
>2. Índices recomendados
>```SQL
>CREATE INDEX idx_kardex_weighted_product
>ON kardex_ponderado (product_id);
>```
>```SQL
>CREATE INDEX idx_kardex_weighted_date
>ON kardex_ponderado (movement_date);
>```
>```SQL
>CREATE INDEX idx_kardex_weighted_movement
>ON kardex_ponderado (inventory_movement_id);
>```
>
>3. Regla clave del ponderado.
>Fórmula base
>```
>                     (total_valor_actual + nueva_compra) 
>  nuevo_promedio = ---------------------------------------- 
>                     (total_cantidad_actual + nueva_cantidad)
>```
>
>4. Importante
>El promedio:
> - Solo cambia en entradas
> - NO cambia en salidas

## Snapshot_inventario | Corte de inventario
**Descripción:** Registra el corte mensual de cada uno de los inventarios de los productos para evitar consultas lentas en la *Inventario_Movimiento*. Estos cortes se deben realizar cada final de mes de manera automática.

| Campo (Laravel / Inglés) | Tu campo original        | Descripción                                                                                                        |
| ------------------------ | ------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| id                       | id_snapshot              | Identificador del corte de inventario <br> *Inventory snapshot identifier*                                         |
| product_id               | fk_producto_snapshot     | Referencia al producto <br> *Reference to the product*                                                             |
| snapshot_date            | fecha_corte_snapshot     | Fecha del corte del inventario <br> *Inventory snapshot date*                                                      |
| final_quantity           | cant_final_snapshot      | Cantidad final del producto en la fecha de corte <br> *Final product quantity at snapshot date*                    |
| fifo_cost                | costo_fifo_snapshot      | Costo total del inventario bajo método FIFO (ojo al nombre original) <br> *Total inventory cost using FIFO method* |
| weighted_cost            | costo_ponderado_snapshot | Costo total bajo promedio ponderado <br> *Total inventory cost using weighted average method*                      |

>[!NOTE]
>Índices:
>```SQL
>   CREATE UNIQUE INDEX unique_snapshot
>   ON inventory_snapshots (product_id, snapshot_date);
>```
>```SQL
>   CREATE INDEX idx_snapshot_product
>   ON inventory_snapshots (product_id);
>```
>```SQL
>   CREATE INDEX idx_snapshot_date
>   ON inventory_snapshots (snapshot_date);
>```

## Stock_actual | Stock actual
**Descripción:** Se basa en la cantidad del stock actual de cada producto basado en la llamada Movimiento_inventario, con el fin de obtener el saldo de cada producto en tiempo real

| Campo (Laravel / Inglés) | Tu campo original | Descripción                                                                     |
| ------------------------ | ----------------- | ------------------------------------------------------------------------------- |
| id                       | id_stock          | Identificador del registro de stock <br> *Stock record identifier*              |
| product_id               | fk_producto       | Referencia al producto <br> *Reference to the product*                          |
| quantity                 | cant_stock        | Cantidad actual disponible del producto <br> *Current available stock quantity* |

>[!NOTE]
>Esta tabla tiene dos enfoques dependiendo de la fase
>
>*FASE 1 (Tabla de verdad)*
>```
>   stock_actual = fuente de verdad del inventario
>```
>
>*FASE 2 (cuando se implemente inventario real)*
>```
>   inventory_movements = fuente de verdad
>   stock_actual = cache optimizado
>```
>
>*Índice:*
>```SQL
>UNIQUE (product_id)
>```

## Cotizacion_master | Cotización (encabezado)

**Descripción:** Al igual que la *Compra_master*, almacena los datos generales de la Cotización

| Campo (Laravel / Inglés) | Tu campo original    |                                      Descripción                                      |
|--------------------------|----------------------|:-------------------------------------------------------------------------------------:|
| id                       | id_cotizacion_master | Identificador de la cotización   *Quotation identifier*                               |
| quotation_number         | numero_cotizacion    | Número de la cotización   *Quotation number*                                          |
| customer_id              | fk_cliente           | Cliente al que se le realiza la cotización   *Customer reference*                     |
| quotation_date           | fecha_cotizacion     | Fecha de la cotización   *Quotation date*                                             |
| expiration_date          | fecha_vencimiento    | Fecha de vencimiento de la cotización   *Quotation expiration date*                   |
| subtotal                 | subtotal_cotizacion  | Subtotal antes de descuentos e impuestos   *Subtotal before discounts and taxes*      |
| discount_amount          | total_descuento      | Valor total de descuentos   *Total discount amount*                                   |
| tax_amount               | total_impuesto       | Valor total de impuestos   *Total tax amount*                                         |
| total_amount             | total_cotizacion     | Valor total de la cotización   *Total quotation amount*                               |
| status                   | estado_cotizacion    | Estado de la cotización (ver las opciones en las notas de abajo)   *Quotation status* |
| notes                    | observaciones        | Observaciones generales   *General notes*                                             |
| created_by               | creado_por           | Usuario que creó la cotización   *User who created the quotation*                     |
| created_at               | fecha_creacion       | Fecha de creación   *Creation date*                                                   |
| updated_by               | actualizado_por      | Usuario que actualizó la cotización   *User who updated the quotation*                |
| updated_at               | fecha_actualizacion  | Fecha de actualización   *Last update date*                                           |

>[!NOTE]
>Estado de la cotización (*status*)
>
>| Estado    | Significado        |
>| --------- | ------------------ |
>| DRAFT     | Borrador           |
>| SENT      | Enviada            |
>| APPROVED  | Aprobada           |
>| REJECTED  | Rechazada          |
>| EXPIRED   | Vencida            |
>| CONVERTED | Convertida a venta |
>
>**Validaciones**
>```SQL
>    CHECK (subtotal >= 0),
>    CHECK (total_descuento >= 0),
>    CHECK (total_cotizacion >= 0)
>```
>
>**Índices recomendados**
>```SQL
>CREATE UNIQUE INDEX idx_quotation_number
>ON quotation_master (quotation_number);
>```
>```SQL
>CREATE INDEX idx_quotation_customer
>ON quotation_master (customer_id);
>```
>```SQL
>CREATE INDEX idx_quotation_date
>ON quotation_master (quotation_date);
>```
>
>**Reglas importantes**
>Coherencia
>```
>total_amount = subtotal - discount + tax
>```
>Fecha de vencimiento
>```
>expiration_date >= quotation_date
>```

## Cotizacion_Detalle

**Descripción:** Se relaciona el detalle de cada producto cotizado al cliente.

| Campo (Laravel / Inglés) | Tu campo original             | Descripción                                                                  |
|--------------------------|-------------------------------|------------------------------------------------------------------------------|
| id                       | id_cotizacion_detalle         | Identificador del detalle   *Quotation detail identifier*                    |
| quotation_id             | fk_cotizacion_master          | Relación con la cotización master   *Reference to the quotation*             |
| product_presentation_id  | fk_producto_presentation      | Presentación del producto cotizada   *Reference to the product presentation* |
| quantity                 | cant_cotizacion_detalle       | Cantidad cotizada   *Quoted quantity*                                        |
| unit_price               | valor_unit_cotizacion_detalle | Precio unitario   *Unit price*                                               |
| discount_percentage      | xje_descuento                 | Porcentaje de descuento   *Discount percentage*                              |
| discount_amount          | valor_descuento               | Valor del descuento   *Discount amount*                                      |
| total_amount             | total_cotizacion_detalle      | Total del ítem   *Line total amount*                                         |
| created_by               | creado_por                    | Usuario que creó la cotización   *User who created the quotation*            |
| created_at               | fecha_creacion                | Fecha de creación   *Creation date*                                          |
| updated_by               | actualizado_por               | Usuario que actualizó la cotización   *User who updated the quotation*       |
| updated_at               | fecha_actualizacion           | Fecha de actualización   *Last update date*                                  |

>[!NOTE]
>*Validaciones:*
>```SQL
>  CHECK (quantity > 0)
>  CHECK (unit_price >= 0)
>  CHECK (discount_amount >= 0)
>```
>
>*Índices:*
>```SQL
>  CREATE INDEX idx_quotation_detail_master
>  ON quotation_details (quotation_id);
>```
>```SQL
>  CREATE INDEX idx_quotation_detail_product
>  ON quotation_details (product_presentation_id);
>```
>
>Índice compuesto
>```SQL
>  CREATE INDEX idx_quotation_product
>  ON quotation_details (quotation_id, product_presentation_id);
>```
>
>Evitar duplicados
>```SQL
>  UNIQUE (quotation_id, product_presentation_id)
>```

## Modulo
**Descripción:** Almacena el nombre de cada uno de los módulos visibles para el usuario
| Campo | Descripción |
|-------|-------------|
| id_modulo | Identificador del módulo |
| nombre_modulo | Nombre del módulo |

| Campo (Laravel / Inglés) |  Tu campo original  |                                 Descripción                                |
|:------------------------:|:-------------------:|:--------------------------------------------------------------------------:|
| id                       | id_modulo           | Identificador del módulo   *Module identifier*                             |
| code                     | codigo_modulo       | identificador técnico                                                      |
| name                     | nombre_modulo       | Nombre del módulo   *Module name*                                          |
| icon                     | icono               | UI                                                                         |
| is_active                | estado_modulo       | Indica si el módulo está activo   *Indicates whether the module is active* |
| route                    | ruta                | ruta del frontend/backend                                                  |
| order                    | orden               | orden en menú                                                              |
| created_by               | creado_por          | Usuario que creó la cotización   *User who created the quotation*          |
| created_at               | fecha_creacion      | Fecha de creación   *Creation date*                                        |
| updated_by               | actualizado_por     | Usuario que actualizó la cotización   *User who updated the quotation*     |
| updated_at               | fecha_actualizacion | Fecha de actualización   *Last update date*                                |

>[!NOTE]
>*Índices:*
>```SQL
>CREATE UNIQUE INDEX idx_module_name
>ON modules (name);
>```
>```SQL
>CREATE INDEX idx_module_active
>ON modules (is_active);
>```

## Permisos_Usuario_Modulo
**Descripción:** Almacena la relación de los permisos de tiene cada usuario con respecto a cada uno de los módulos visible en el software web

| Campo (Laravel / Inglés) | Tu campo original         | Descripción                                                         |
| ------------------------ | ------------------------- | ------------------------------------------------------------------- |
| id                       | id_permiso_usuario_modulo | Identificador del permiso <br> *User-module permission identifier*  |
| user_id                  | fk_usuario                | Usuario al que se le asigna el permiso <br> *Reference to the user* |
| module_id                | fk_modulo                 | Módulo al que aplica el permiso <br> *Reference to the module*      |
| can_create               | crear                     | Permite crear registros <br> *Allows creating records*              |
| can_read                 | leer                      | Permite ver información <br> *Allows reading data*                  |
| can_update               | actualizar                | Permite editar registros <br> *Allows updating records*             |
| can_delete               | eliminar                  | Permite eliminar registros <br> *Allows deleting records*           |
| created_by               | creado_por          | Usuario que creó la cotización   *User who created the quotation*          |
| created_at               | fecha_creacion      | Fecha de creación   *Creation date*                                        |
| updated_by               | actualizado_por     | Usuario que actualizó la cotización   *User who updated the quotation*     |
| updated_at               | fecha_actualizacion | Fecha de actualización   *Last update date*                                |

>[!NOTE]
>*Índices*
>```SQL
>   CREATE INDEX idx_permission_user
>   ON user_module_permissions (user_id);
>```
>```SQL
>   CREATE INDEX idx_permission_module
>   ON user_module_permissions (module_id);
>```
>
>*Índice único*
>```SQL
>   CREATE UNIQUE INDEX unique_user_module
>   ON user_module_permissions (user_id, module_id);
>```

## Datos_empresa
**Descripción:** Almacena los datos de la empresa que hace uso del software para mostrarlo en los reportes.

| Campo (Laravel / Inglés) | Tu campo original   | Descripción                                                                                                                              |
| ------------------------ | ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| id                       | id_de               | Identificador del registro <br> *Company data identifier*                                                                                |
| business_name            | razon_social_de     | Razón social de la empresa <br> *Company legal name*                                                                                     |
| slogan                   | slogan              | Frase utilizada por la empresa para conectar con los clientes <br> *Company slogan used for branding*                                    |
| tax_id                   | nit_de              | NIT de la empresa <br> *Company tax identification number*                                                                               |
| tax_regime               | tipo_regimen        | Tipo de régimen (simplificado o común) <br> *Tax regime type (simplified or general)*                                                    |
| address                  | direccion_de        | Dirección de la empresa <br> *Company address*                                                                                           |
| phone                    | tel_de              | Teléfono de la empresa <br> *Company phone number*                                                                                       |
| whatsapp                 | whatsapp_de         | Número de WhatsApp de la empresa <br> *Company WhatsApp number*                                                                          |
| email                    | email_de            | Correo electrónico de la empresa <br> *Company email address*                                                                            |
| logo                     | logo_de             | Nombre o ruta de la imagen del logo <br> *Company logo file name or path*                                                                |
| sale_percentage          | xje_venta_de        | Porcentaje de venta utilizado para calcular precios automáticamente <br> *Default sales percentage used for automatic price calculation* |
| user_id                  | fk_usuario          | Usuario relacionado al registro <br> *Reference to the user*                                                                             |
| created_by               | creado_por          | Usuario que creó el registro <br> *User who created the record*                                                                          |
| created_at               | fecha_creacion      | Fecha de creación <br> *Creation date*                                                                                                   |
| updated_by               | actualizado_por     | Usuario que actualizó el registro <br> *User who updated the record*                                                                     |
| updated_at               | fecha_actualizacion | Fecha de actualización <br> *Last update date*                                                                                           |

| Campo | Descripción |
|-------|-------------|
| id_de | Identificador del registro |
| razon_social_de | Razón social de la empresa |
| slogan | slogan_empresa | Frase utilizada por la empresa para conectar con los clientes |
| nit_de | Nit de la empresa |
| tipo_regimen | Simplificado o común |
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
   
   ### Cotizacion_master
   ```SQL
   -- Consultas por cotización
   CREATE INDEX idx_cotizacion_fecha
   ON cotizacion_master (fecha_hora);
   
   -- Consultas por cliente
   CREATE INDEX idx_cotizacion_cliente
   ON cotizacion_master (fk_cliente);
   ```
   
   ### Cotizacion_detalle
   ```SQL
   -- Detalle por cotización
   CREATE INDEX idx_cotizacion_detalle_master
   ON cotizacion_detalle (fk_cotizacion_master);
   
   -- Historial por producto
   CREATE INDEX idx_cotizacion_detalle_producto
   ON cotizacion_detalle (fk_producto);
   ```
      
   ## Resultado de Indexes:

   |                     | Índice                             |
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
   | cotizacion_master         | fecha_hora                         |
   | cotizacion_master         | fk_cliente                         |
   | cotizacion_detalle        | fk_cotizacion_master               |
   | cotizacion_detalle        | fk_producto                        |
  
* Crear nuevo archivo markdown para los diagramas de flujo al momento de realizar una compra o venta de un producto. ya que este movimiento toca muchas tablas en secuencia
