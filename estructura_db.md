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

## Categories | Categorías

**Descripción:** Contiene las categorías generales para clasificar las subcategorias.  
**Ejemplo:** Tecnología, Belleza, Papeleria...

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

## Compra_detalle

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
>Indices a crear:
>```SQL
>  CREATE INDEX idx_purchase_detail_purchase
>  ON purchase_details (purchase_id);
>
>  CREATE INDEX idx_purchase_detail_product
>  ON purchase_details (product_presentation_id);
>```

## Abono_compra

**Descripción:** Esta almacena los diferentes nombres de los archivos adjuntos que son comprobantes de abonos realizados o pago total. Según esta se puede saber la cantidad de veces que ha abonado al proveedor sobre la misma factura 

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

## Devolucion_compra

**Descripción:** Esta relaciona los productos que se devuelven al proveedor con su respectiva justificación.

| Campo | Descripción |
|-------|-------------|
| id_devolucion_compra | Identificador de la devolución |
| fk_compra_detalle | Llave foránea de la factura Compra Detalle para obtener datos no solo del producto, si no datos adicionales de la compra master
| fecha_hora_devolucion_compra | Fecha de la devolución |
| cant_devolucion_compra | Cantidad devuelta del producto |
| estado_devolucion_compra | (0) Si está pendiente (1) si ya se realizó la devolución |
| observaciones_devolucion_compra | Justificación de la devolución |

## Usuario

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

## Cliente
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
| fk_ciudad | Referencia a la Ciudad |

## Empleado_cliente

**Descripción:** Registra los nombres de los empleados que trabajan para los clientes corporativos que solicitan los productos. Pensado en la trazabilidad de las solicitudes en compras a cŕedito.

| Campo | Descripción |
|-------|-------------|
| id_empleado_cliente | Identificador del empleado del cliente |
| fk_cliente | Referencia al cliente corporativo |
| cedula_empleado_cliente | Cédula del empleado |
| nombre_empleado_cliente | Nombre del empleado |
| tel_empleado_cliente | Teléfono del empleado |

## Venta_master

**Descripción:** Al igual que la *Compra_master*, almacena los datos generales de la Venta

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

## Venta_detalle

**Descripción:** Se relaciona el detalle de cada producto vendido al cliente, la razón por la cual se relaciona el usuario en esta se debe a las ventas a *crédito* que se pueden realizar a un cliente en diferentes fechas, y por lo tanto, pudo venderse el producto por empleados diferentes.

| Campo | Descripción |
|-------|-------------|
| id_venta_detalle | Identificador del detalle de venta |
| fk_venta_master | Referencia a venta_master |
| fk_producto_presentation | Referencia a las tablas producto y a la presentación del mismo |
| fk_presentacion_types | Se requiere una columna para indicar la presentacion |
| cant_venta_detalle | Cantidad vendida |
| valor_unit_venta_detalle | Valor unitario vendido |
| discount_value| valor_descuento_producto | Descuento únicamente del producto |
| total_venta_detalle | Total del detalle |
| creado_por | Usuario que creó el registro |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro |
| fecha_actualizacion | Fecha de actualización del registro |

## Devolucion_venta

**Descripción:** Esta relaciona los productos que se devuelven por parte del cliente con su respectiva justificación.

| Campo | Descripción |
|-------|-------------|
| id_devolucion_venta | Identificador de la devolución |
| fk_venta_detalle | Llave foránea de la factura Venta Detalle para obtener datos no solo del producto, si no datos adicionales de la venta master
| fecha_hora_devolucion_venta | Fecha de la devolución |
| cant_devolucion_venta | Cantidad devuelta del producto |
| observaciones_devolucion_venta | Justificación de la devolución |

## Abono_venta
**Descripción:** Esta almacena los diferentes nombres de los archivos adjuntos que son comprobantes de abonos realizados o pago total. Según esta se puede saber la cantidad de veces que ha abonado un cliente a la misma factura 

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

## Movimiento_inventario
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
| fk_ubicacion | Referencia a la ubicación|
| id_grupo_movimiento | Se usa para agrupar movimientos que pertenecen a una misma operación (compra distribuida, venta, traslado, ajuste, etc.) |
| observaciones | En caso de haber devoluciones, ajustes, traslados, se debe especificar la razón por la que se dió este movimiento|

>[!NOTE]
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

## Inventario_capas
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

## Inventario_salida_detalle
**Descripción:** Registra el detalle del consumo de inventario por capas para cada venta, 
permitiendo identificar el costo real de los productos vendidos según el método de costeo (FIFO, o Ponderado).
| Campo | Descripción |
|-------|-------------|
| id_salida_detalle | Identificador de la salida|
| fk_venta_detalle  | Llave foránea de la venta_detalle |
| fk_capa           | Llave foránea de la inventario_capas |
| fk_producto       | Llave foránea de la producto (para agilizar consultas) |
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

## Kardex_fifo
**Descripción:** Mantiene actualizado el inventario FIFO

| Campo | Descripción |
|-------|-------------|
| id_kardex_fifo | id de la |
| fk_inventario | Referencia al id del inventario para obtener datos de las otras entidades como producto, compra_detalle, venta_detalle |
| cant_entrada | Cantidad que ingresa |
| cant_salida | Cantidad que egresa |
| cant_saldo | Cantidad restante |
| valor_saldo | Valor actual del inventario |
| fecha_movimiento | Fecha del movimiento |

## Kardex_ponderado
**Descripción:** Mantiene actualizado el inventario PONDERADO

| Campo | Descripción |
|-------|-------------|
| id_kardex_ponderado | id de la |
| fk_inventario | Referencia al id del inventario para obtener datos de las otras entidades como producto, compra_detalle, venta_detalle |
| cant_entrada | Cantidad que ingresa |
| cant_salida | Cantidad que egresa |
| cant_saldo | Cantidad restante |
| valor_saldo | Valor actual del inventario |
| fecha_movimiento | Fecha del movimiento |

## Snapshot_inventario
**Descripción:** Registra el corte mensual de cada uno de los inventarios de los productos para evitar consultas lentas en la *Inventario_Movimiento*

| Campo | Descripción |
|-------|-------------|
| id_snapshot | Identificador del corte del inventario |
| fecha_corte_snapshot | Fecha del corte es la misma fecha de creación |
| fk_producto_snapshot | Referencia del producto |
| cant_final_snapshot | cantidad final del producto |
| costo_lifo_snapshot | Costo final del inventario LIFO |
| costo_ponderado_snapshot | Costo final del inventario Ponderado |

## Stock_actual
**Descripción:** Se basa en la cantidad del stock actual de cada producto basado en la llamada Movimiento_inventario, con el fin de obtener el saldo de cada producto en tiempo real

| Campo | Descripción |
|-------|-------------|
| id_stock | Identificador del registro |
| fk_producto | Referencia al producto |
| cant_stock | Cantidad actual del producto |

## Cotizacion_master

**Descripción:** Al igual que la *Compra_master*, almacena los datos generales de la Cotización

| Campo | Descripción |
|-------|-------------|
| id_cotizacion_master | Identificador de la cotización |
| numero_cotizacion | Número consecutivo de la cotización |
| fk_cliente | Referencia al cliente |
| fecha_hora | Fecha de la factura |
| subtotal | Suma total de los registros vendidos |
| total_descuento | Suma total de descuentos |
| total_cotizacion | Valor total después del descuento |
| observaciones | Observaciones de la venta |
| estado_cotizacion | ENUM('BORRADOR','APROBADA','RECHAZADA','VENCIDA') |
| creado_por | Usuario que actualizó el registro |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro |
| fecha_actualizacion | Fecha de actualización del registro |

>[!NOTE]
>NOTAS SQL
>```SQL
> CREATE TABLE cotizacion_master (
>    id_cotizacion_master SERIAL PRIMARY KEY,
>    numero_cotizacion VARCHAR(50) NOT NULL UNIQUE,
>
>    fk_cliente INT NOT NULL,
>
>    fecha_hora TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
>
>    subtotal NUMERIC(14,2) NOT NULL DEFAULT 0,
>    total_descuento NUMERIC(14,2) NOT NULL DEFAULT 0,
>    total_cotizacion NUMERIC(14,2) NOT NULL DEFAULT 0,
>
>    observaciones TEXT,
>
>    creado_por INT,
>    fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
>    actualizado_por INT,
>    fecha_actualizacion TIMESTAMP,
>
>    -- 🔗 Relaciones
>    CONSTRAINT fk_cotizacion_cliente 
>        FOREIGN KEY (fk_cliente) REFERENCES cliente(id_cliente),
>
>    CONSTRAINT fk_cotizacion_creado_por 
>        FOREIGN KEY (creado_por) REFERENCES usuario(id_usuario_sistema),
>
>    CONSTRAINT fk_cotizacion_actualizado_por 
>        FOREIGN KEY (actualizado_por) REFERENCES usuario(id_usuario_sistema),
>
>    -- 🔒 Validaciones
>    CHECK (subtotal >= 0),
>    CHECK (total_descuento >= 0),
>    CHECK (total_cotizacion >= 0)
> );
>```

## Cotizacion_Detalle

**Descripción:** Se relaciona el detalle de cada producto cotizado al cliente.

| Campo | Descripción |
|-------|-------------|
| id_cotizacion_detalle | Identificador del detalle de la cotización |
| fk_cotizacion_master | Referencia a la cotizacion_master |
| fk_producto | Referencia al producto vendido |
| fk_producto_presentacion | Referencia de la presentacion del producto |
| cant_cotizacion_detalle | Cantidad cotizada |
| valor_unit_cotizacion_detalle | Valor unitario cotizado |
| total_cotizacion_detalle | Total del detalle |
| creado_por | Usuario que creó el registro |
| fecha_creacion | Fecha de creación del registro |
| actualizado_por | Usuario que actualizó el registro |
| fecha_actualizacion | Fecha de actualización del registro |

>[!NOTE]
>Notas SQL
>```SQL
>CREATE TABLE cotizacion_detalle (
>    id_cotizacion_detalle SERIAL PRIMARY KEY,
>    
>    fk_cotizacion_master INT NOT NULL,
>    fk_producto INT NOT NULL,
>    fk_producto_presentacion INT NOT NULL,
>    
>    cant_cotizacion_detalle NUMERIC(14,2) NOT NULL,
>    valor_unit_cotizacion_detalle NUMERIC(14,2) NOT NULL,
>    total_cotizacion_detalle NUMERIC(14,2) NOT NULL,
>    
>    creado_por INT,
>    fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
>    actualizado_por INT,
>    fecha_actualizacion TIMESTAMP,
>    
>    -- 🔗 Relaciones
>    CONSTRAINT fk_detalle_cotizacion 
>        FOREIGN KEY (fk_cotizacion_master) 
>        REFERENCES cotizacion_master(id_cotizacion_master)
>        ON DELETE CASCADE,
>
>    CONSTRAINT fk_detalle_producto 
>        FOREIGN KEY (fk_producto) 
>        REFERENCES producto(id_producto),
>
>    CONSTRAINT fk_detalle_producto_presentacion 
>        FOREIGN KEY (fk_producto_presentacion) 
>        REFERENCES producto_presentacion(id_producto_presentacion),
>
>    CONSTRAINT fk_detalle_creado_por 
>        FOREIGN KEY (creado_por) REFERENCES usuario(id_usuario_sistema),
>
>    CONSTRAINT fk_detalle_actualizado_por 
>        FOREIGN KEY (actualizado_por) REFERENCES usuario(id_usuario_sistema),
>
>    -- 🔒 Validaciones
>    CHECK (cant_cotizacion_detalle > 0),
>    CHECK (valor_unit_cotizacion_detalle >= 0),
>    CHECK (total_cotizacion_detalle = cant_cotizacion_detalle * valor_unit_cotizacion_detalle)
>);
>```

## Modulo
**Descripción:** Almacena el nombre de cada uno de los módulos visibles para el usuario
| Campo | Descripción |
|-------|-------------|
| id_modulo | Identificador del módulo |
| nombre_modulo | Nombre del módulo |

## Permisos_Usuario_Modulo
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

## Datos_empresa
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
