---
title: 'Intercambio de campos de registros: Funcionamiento de RFX'
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
ms.openlocfilehash: 903acf4f55fb2708f4998a2babf3f143c895429b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367171"
---
# <a name="record-field-exchange-how-rfx-works"></a>Intercambio de campos de registros: Funcionamiento de RFX

En este tema se explica el proceso RFX. Este es un tema avanzado que cubre:

- [RFX y el conjunto de registros](#_core_rfx_and_the_recordset)

- [El proceso RFX](#_core_the_record_field_exchange_process)

> [!NOTE]
> Este tema se aplica a clases derivadas de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usa la obtención masiva de filas, se implementará el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, vea [Conjunto de registros: obtención de registros en masa (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX y el conjunto de registros

Los miembros de datos de campo del objeto de conjunto de registros, tomados en conjunto, constituyen un búfer de edición que contiene las columnas seleccionadas de un registro. Cuando el conjunto de registros se abre por primera vez y está a punto de leer el primer registro, RFX enlaza (asocia) cada columna seleccionada a la dirección del miembro de datos de campo adecuado. Cuando el conjunto de registros actualiza un registro, RFX llama a funciones de la API ODBC para enviar una instrucción **UPDATE** o **INSERT** de SQL al controlador. RFX utiliza su conocimiento de los miembros de datos de campo para especificar las columnas que se van a escribir.

El marco de trabajo realiza una copia de seguridad del búfer de edición en determinadas etapas para que pueda restaurar su contenido si es necesario. RFX realiza una copia de seguridad del búfer de edición antes de agregar un nuevo registro y antes de editar un registro existente. Restaura el búfer de edición en algunos `Update` casos, `AddNew`por ejemplo, después de una llamada siguiente. El búfer de edición no se restaura si abandona un búfer de `Update`edición recién cambiado, por ejemplo, pasando a otro registro antes de llamar a .

Además de intercambiar datos entre el origen de datos y los miembros de datos de campo del conjunto de registros, RFX administra los parámetros de enlace. Cuando se abre el conjunto de registros, los miembros de datos de `CRecordset::Open` parámetro se enlazan en el orden de los marcadores de posición "?" en la instrucción SQL que se construye. Para obtener más información, vea [Conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

La invalidación de `DoFieldExchange` la clase de conjunto de registros hace todo el trabajo, moviendo datos en ambas direcciones. Al igual que el intercambio de datos de cuadro de diálogo (DDX), RFX necesita información sobre los miembros de datos de la clase. El asistente proporciona la información necesaria escribiendo `DoFieldExchange` una implementación específica del conjunto de registros de usted, en función de los nombres de miembro de datos de campo y los tipos de datos que especifique con el asistente.

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Proceso de intercambio de campos de registro

En esta sección se describe la secuencia de eventos RFX a medida que se abre un objeto de conjunto de registros y a medida que se agregan, actualizan y eliminan registros. La tabla [Secuencia de operaciones RFX durante](#_core_sequence_of_rfx_operations_during_recordset_open) el conjunto de registros abierto y la secuencia de tabla de [operaciones RFX durante](#_core_sequence_of_rfx_operations_during_scrolling) el desplazamiento en este tema muestran el proceso mientras RFX procesa un `Move` comando en el conjunto de registros y RFX administra una actualización. Durante estos procesos, [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) se llama para realizar muchas operaciones diferentes. El `m_nOperation` miembro de datos de la [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto determina qué operación se solicita. Puede resultarle útil leer [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) y [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) antes de leer este material.

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX: Enlace inicial de columnas y parámetros

Las siguientes actividades RFX se producen, en el orden que se muestra, cuando se llama a la función miembro [Open](../../mfc/reference/crecordset-class.md#open) de un objeto de conjunto de registros:

- Si el conjunto de registros `DoFieldExchange` tiene miembros de datos de parámetro, el marco de trabajo llama para enlazar los parámetros a marcadores de posición de parámetro en la cadena de instrucción SQL del conjunto de registros. Se utiliza una representación dependiente del tipo de datos del valor del parámetro para cada marcador de posición que se encuentra en la instrucción **SELECT.** Esto ocurre después de preparar la instrucción SQL, pero antes de que se ejecute. Para obtener información acerca `::SQLPrepare` de la preparación de instrucciones, vea la función en la *referencia del programador*ODBC .

- El marco `DoFieldExchange` de trabajo llama por segunda vez para enlazar los valores de las columnas seleccionadas a los miembros de datos de campo correspondientes en el conjunto de registros. Esto establece el objeto de conjunto de registros como un búfer de edición que contiene las columnas del primer registro.

- El conjunto de registros ejecuta la instrucción SQL y el origen de datos selecciona el primer registro. Las columnas del registro se cargan en los miembros de datos de campo del conjunto de registros.

En la tabla siguiente se muestra la secuencia de operaciones RFX al abrir un conjunto de registros.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Secuencia de operaciones RFX durante el conjunto de registros abierto

|La operación|Operación DoFieldExchange|Funcionamiento de la base de datos/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Abra el conjunto de registros.|||
||2. Cree una instrucción SQL.||
|||3. Envíe el SQL.|
||4. Enlazar miembros de datos de parámetros.||
||5. Enlazar miembros de datos de campo a columnas.||
|||6. ODBC realiza el movimiento y rellena los datos.|
||7. Fije los datos para C++.||

Los conjuntos de registros usan la ejecución preparada de ODBC para permitir una consulta rápida con la misma instrucción SQL. Para obtener más información acerca de la ejecución preparada, vea la *referencia del programador del* SDK de ODBC en MSDN Library.

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX: Desplazamiento

Cuando se desplaza de un registro `DoFieldExchange` a otro, el marco de trabajo llama para reemplazar los valores almacenados anteriormente en los miembros de datos de campo con valores para el nuevo registro.

En la tabla siguiente se muestra la secuencia de operaciones RFX cuando el usuario se mueve de un registro a otro.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Secuencia de operaciones RFX durante el desplazamiento

|La operación|Operación DoFieldExchange|Funcionamiento de la base de datos/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. `MoveNext` Llame o una de las otras funciones Move.|||
|||2. ODBC realiza el movimiento y rellena los datos.|
||3. Fije los datos para C++.||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: Adición de nuevos registros y edición de registros existentes

Si agrega un nuevo registro, el conjunto de registros funciona como un búfer de edición para generar el contenido del nuevo registro. Al igual que con la adición de registros, la edición de registros implica cambiar los valores de los miembros de datos de campo del conjunto de registros. Desde la perspectiva de RFX, la secuencia es la siguiente:

1. La llamada a la función miembro [AddNew](../../mfc/reference/crecordset-class.md#addnew) o [Edit](../../mfc/reference/crecordset-class.md#edit) del conjunto de registros hace que RFX almacene el búfer de edición actual para que se pueda restaurar más adelante.

1. `AddNew`o `Edit` prepara los campos en el búfer de edición para que RFX pueda detectar los miembros de datos de campo modificados.

   Dado que un nuevo registro no tiene valores `AddNew` anteriores con los que comparar los nuevos, establece el valor de cada miembro de datos de campo en un valor de PSEUDO_NULL. Más adelante, `Update`cuando se llama a , RFX compara el valor de cada miembro de datos con el valor de PSEUDO_NULL. Si hay una diferencia, se ha establecido el miembro de datos. (PSEUDO_NULL no es lo mismo que una columna de registro con un valor Null verdadero ni ninguno de estos es el mismo que C++ NULL.)

   A `Update` diferencia `AddNew`de `Update` la `Edit` llamada a , la llamada para compara los valores actualizados con los valores almacenados anteriormente en lugar de usar PSEUDO_NULL. La diferencia `AddNew` es que no tiene valores almacenados previamente para la comparación.

1. Establezca directamente los valores de los miembros de datos de campo cuyos valores desea editar o que desee rellenar para un nuevo registro. Esto puede `SetFieldNull`incluir llamar a .

1. La llamada a [Update](../../mfc/reference/crecordset-class.md#update) comprueba los miembros de datos de campo modificados, como se describe en el paso 2 (consulte la tabla [Secuencia de operaciones RFX durante](#_core_sequence_of_rfx_operations_during_scrolling)el desplazamiento ). Si ninguno ha `Update` cambiado, devuelve 0. Si algunos miembros de `Update` datos de campo han cambiado, prepara y ejecuta una instrucción **SQL INSERT** que contiene valores para todos los campos actualizados del registro.

1. Para `AddNew` `Update` , concluye restaurando los valores almacenados previamente `AddNew` del registro que era actual antes de la llamada. Para `Edit`, los nuevos valores editados permanecen en su lugar.

En la tabla siguiente se muestra la secuencia de operaciones RFX al agregar un nuevo registro o editar un registro existente.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Secuencia de operaciones RFX durante AddNew y Edit

|La operación|Operación DoFieldExchange|Funcionamiento de la base de datos/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. `AddNew` Llame `Edit`o .|||
||2. Realice una copia de seguridad del búfer de edición.||
||3. `AddNew`Para , marque los miembros de datos de campo como "limpios" y Null.||
|4. Asigne valores a los miembros de datos de campo de conjunto de registros.|||
|5. `Update`Llame a .|||
||6. Compruebe si hay campos modificados.||
||7. Cree una `AddNew` instrucción SQL **INSERT** para o la instrucción **UPDATE** para `Edit`.||
|||8. Envíe el SQL.|
||9. `AddNew`Para , restaure el búfer de edición a su contenido de copia de seguridad. Para `Edit`, elimine la copia de seguridad.||

### <a name="rfx-deleting-existing-records"></a>RFX: Eliminación de registros existentes

Al eliminar un registro, RFX establece todos los campos en NULL como un recordatorio de que el registro se elimina y debe salir de él. No necesita ninguna otra información de secuencia RFX.

## <a name="see-also"></a>Consulte también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Consumidor ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Macros, funciones globales y variables globales](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Clase CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
