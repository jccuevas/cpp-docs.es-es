---
title: 'Intercambio de campos de registro: Funcionamiento de RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
ms.openlocfilehash: 7da9d480f16dcb6bc5ded0a1dff559b1b1ac4b38
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032682"
---
# <a name="record-field-exchange-how-rfx-works"></a>Intercambio de campos de registro: Funcionamiento de RFX

En este tema se explica el proceso RFX. Esto es un avanzado cobertura del tema:

- [RFX y el conjunto de registros](#_core_rfx_and_the_recordset)

- [El proceso RFX](#_core_the_record_field_exchange_process)

> [!NOTE]
>  En este tema se aplica a las clases derivadas de `CRecordset` en qué fila de forma masiva captura no se ha implementado. Si usas la obtención masiva de filas, se implementa el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, consulte [conjunto de registros: Obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_rfx_and_the_recordset"></a> RFX y el conjunto de registros

Los miembros de datos de campo del objeto de conjunto de registros, tomados en conjunto, constituyen un búfer de edición que contiene las columnas seleccionadas de un registro. Cuando el conjunto de registros se abre por primera vez y está a punto de leer el primer registro, RFX enlaza (asocia) cada una de las columnas seleccionadas a la dirección del miembro de datos de campo correspondiente. Cuando el conjunto de registros actualiza un registro, RFX llama a funciones de API de ODBC para enviar una instancia de SQL **actualización** o **insertar** instrucción del controlador. RFX utiliza su conocimiento de los miembros de datos de campo para especificar las columnas que se va a escribir.

El marco de trabajo realiza copias de seguridad del búfer de edición en determinadas fases para poder restaurar su contenido si es necesario. RFX realiza copias de seguridad del búfer de edición antes de agregar un nuevo registro y antes de editar un registro existente. Restaura el búfer de edición en algunos casos, por ejemplo, después de un `Update` llamada siguiente `AddNew`. No se restaura el búfer de edición si se deja un búfer recién modificado por, por ejemplo, mover a otro registro antes de llamar a `Update`.

Además de intercambiar datos entre el origen de datos y los miembros de datos de campo del conjunto de registros, RFX administra los parámetros de enlace. Cuando se abre el conjunto de registros, los miembros de datos de parámetro se enlazan en el orden de los "?" marcadores de posición en la instrucción SQL que `CRecordset::Open` construye. Para obtener más información, consulte [conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

La invalidación de la clase de conjunto de registros `DoFieldExchange` realiza todo el trabajo, moviendo los datos en ambas direcciones. Al igual que el intercambio de datos de cuadro de diálogo (DDX), RFX necesita información sobre los miembros de datos de la clase. El asistente proporciona la información necesaria mediante la escritura de una implementación específica del conjunto de registros de `DoFieldExchange` , en función de los datos del campo miembro nombres y tipos de datos especificados mediante el asistente.

##  <a name="_core_the_record_field_exchange_process"></a> Proceso de registro de Exchange de campo

Esta sección describe la secuencia de eventos RFX al abrirse un objeto de conjunto de registros y agregar, actualizar y eliminar registros. La tabla [secuencia de RFX operaciones durante el conjunto de registros abierto](#_core_sequence_of_rfx_operations_during_recordset_open) y la tabla [secuencia de operaciones RFX durante el desplazamiento](#_core_sequence_of_rfx_operations_during_scrolling) en este tema se muestra el proceso como procesos RFX un `Move` comando en el conjunto de registros y administra una actualización. Durante estos procesos, [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) se llama para realizar muchas operaciones diferentes. El `m_nOperation` miembro de datos de la [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto determina qué operación se solicita. Le resultará útil leer [conjunto de registros: ¿Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) y [conjunto de registros: Cómo actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) antes de leer este material.

###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX: Enlace inicial de columnas y parámetros

Se producen las siguientes actividades RFX, en el orden en que se muestra cuando se llama a un objeto recordset [abierto](../../mfc/reference/crecordset-class.md#open) función miembro:

- Si el conjunto de registros tiene miembros de datos de parámetro, el marco llama a `DoFieldExchange` para enlazar los parámetros a los marcadores de posición en la cadena de instrucción SQL del conjunto de registros. Una representación dependen del tipo del valor del parámetro se utiliza para cada marcador de posición de datos se encuentran en la **seleccione** instrucción. Esto se produce después de prepara la instrucción SQL pero antes de ejecutarlo. Para obtener información acerca de la preparación de instrucciones, consulte el `::SQLPrepare` función en ODBC *referencia del programador*.

- Las llamadas de framework `DoFieldExchange` una segunda vez para enlazar los valores de las columnas seleccionadas con los miembros de datos correspondientes en el conjunto de registros. Esto establece el objeto de conjunto de registros como un búfer de edición que contiene las columnas del primer registro.

- El conjunto de registros ejecuta la instrucción SQL y el origen de datos selecciona el primer registro. Las columnas del registro se cargan en los miembros de datos de campo del conjunto de registros.

En la tabla siguiente se muestra la secuencia de operaciones RFX al abrir un conjunto de registros.

### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a> Secuencia de operaciones RFX durante la apertura del conjunto de registros

|La operación|Operación DoFieldExchange|Operación de base de datos/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Abra el conjunto de registros.|||
||2. Generar una instrucción SQL.||
|||3. Enviar la instrucción SQL.|
||4. Enlazar a los miembros de datos de parámetro.||
||5. Enlazar a los miembros de datos a columnas.||
|||6. ODBC realiza el traslado y rellena los datos.|
||7. Corrección de seguridad de los datos de C++.||

Conjuntos de registros utilicen ejecución preparada de ODBC para permitir volver a consultar rápido con la misma instrucción SQL. Para obtener más información sobre la ejecución preparada, vea el SDK de ODBC *referencia del programador* en MSDN Library.

###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX: Desplazarse

Cuando se desplaza de un registro a otro, el marco llama a `DoFieldExchange` para reemplazar los valores almacenados previamente en los miembros de datos de campo con los valores para el nuevo registro.

En la tabla siguiente se muestra la secuencia de operaciones RFX cuando el usuario mueve por los registros.

### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a> Secuencia de operaciones RFX durante el desplazamiento

|La operación|Operación DoFieldExchange|Operación de base de datos/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Llamar a `MoveNext` o una de las demás funciones Move.|||
|||2. ODBC realiza el traslado y rellena los datos.|
||3. Corrección de seguridad de los datos de C++.||

###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX: Agregar nuevos registros y editar los registros existentes

Si agrega un nuevo registro, el conjunto de registros funciona como un búfer de edición para generar el contenido del nuevo registro. Al igual que con la adición de registros, editar registros implica cambiar los valores de los miembros de datos de campo del conjunto de registros. Desde la perspectiva RFX, la secuencia es como sigue:

1. La llamada para el conjunto de registros [AddNew](../../mfc/reference/crecordset-class.md#addnew) o [editar](../../mfc/reference/crecordset-class.md#edit) función miembro hace que RFX almacenar el búfer de edición actual, por lo que se puede restaurar más adelante.

1. `AddNew` o `Edit` prepara los campos en el búfer de edición para que RFX pueda detectar los miembros de datos de campo modificados.

   Dado que un nuevo registro no tiene ningún valor anterior para comparar los nuevos, `AddNew` establece el valor de cada miembro de datos de campo en un valor PSEUDO_NULL. Más adelante, cuando se llama a `Update`, RFX compara el valor de cada miembro de datos con el valor PSEUDO_NULL. Si hay una diferencia, se estableció el miembro de datos. (PSEUDO_NULL no es igual a una columna de registro con un valor Null es true ni ninguno de ellos igual que NULL de C++.)

   A diferencia de la `Update` llamar para `AddNew`, `Update` llamar para `Edit` compara los valores actualizados con los valores almacenados previamente en lugar de utilizar PSEUDO_NULL. La diferencia es que `AddNew` no tiene ningún valor almacenado previamente para la comparación.

1. Establecer directamente los valores de los miembros de datos de campo cuyos valores desea editar o que desea rellenar un nuevo registro. Esto puede incluir la llamada `SetFieldNull`.

1. La llamada a [actualización](../../mfc/reference/crecordset-class.md#update) busca los miembros de datos de campo modificados, como se describe en el paso 2 (vea la tabla [secuencia de operaciones RFX durante el desplazamiento](#_core_sequence_of_rfx_operations_during_scrolling)). Si ha cambiado ninguno, `Update` devuelve 0. Si han cambiado algunos miembros de datos de campo, `Update` prepara y ejecuta una instancia de SQL **insertar** instrucción que contiene valores para todos los campos actualizados en el registro.

1. Para `AddNew`, `Update` concluye mediante la restauración de los valores almacenados previamente del registro que era el actual antes del `AddNew` llamar. Para `Edit`, los valores nuevos y modificados permanecen en su lugar.

En la tabla siguiente se muestra la secuencia de operaciones RFX al agregar un nuevo registro o editar un registro existente.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Secuencia de operaciones RFX durante AddNew y Edit

|La operación|Operación DoFieldExchange|Operación de base de datos/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Llame a `AddNew` o `Edit`.|||
||2. Copia de seguridad del búfer de edición.||
||3. Para `AddNew`, marcar los miembros de datos de campo como "limpia" y Null.||
|4. Asignar valores a los miembros de datos de campo de conjunto de registros.|||
|5. Llame a `Update`.|||
||6. Compruebe si hay campos modificados.||
||7. Generar SQL **insertar** instrucción para `AddNew` o **actualización** instrucción para `Edit`.||
|||8. Enviar la instrucción SQL.|
||9. Para `AddNew`, restaurar el búfer de edición con el contenido de la copia de seguridad. Para `Edit`, elimine la copia de seguridad.||

### <a name="rfx-deleting-existing-records"></a>RFX: Eliminar registros existentes

Cuando se elimina un registro, RFX establece todos los campos en NULL como recordatorio de que el registro se elimina y debe salir de él. No es necesario cualquier otra información de secuencia RFX.

## <a name="see-also"></a>Vea también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Macros, funciones globales y variables globales](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange (clase)](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)