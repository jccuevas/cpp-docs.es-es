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
ms.openlocfilehash: 0661e61bceeedc0dd049ef47f5a0a0b71a8d82ed
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213075"
---
# <a name="record-field-exchange-how-rfx-works"></a>Intercambio de campos de registros: Funcionamiento de RFX

En este tema se explica el proceso de RFX. Este es un tema avanzado que abarca:

- [RFX y el conjunto de registros](#_core_rfx_and_the_recordset)

- [El proceso de RFX](#_core_the_record_field_exchange_process)

> [!NOTE]
>  Este tema se aplica a clases derivadas de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usa la obtención masiva de filas, se implementará el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX y el conjunto de registros

Los miembros de datos de campo del objeto de conjunto de registros, tomadas juntos, constituyen un búfer de edición que contiene las columnas seleccionadas de un registro. Cuando el conjunto de registros se abre por primera vez y está a punto de leer el primer registro, RFX enlaza (asocia) cada columna seleccionada a la dirección del miembro de datos de campo correspondiente. Cuando el conjunto de registros actualiza un registro, RFX llama a las funciones de la API de ODBC para enviar una instrucción **Update** o **Insert** de SQL al controlador. RFX usa su conocimiento de los miembros de datos de campo para especificar las columnas que se van a escribir.

El marco de trabajo realiza una copia de seguridad del búfer de edición en determinadas fases para que pueda restaurar su contenido si es necesario. RFX realiza una copia de seguridad del búfer de edición antes de agregar un nuevo registro y antes de editar un registro existente. Restaura el búfer de edición en algunos casos, por ejemplo, después de una llamada a `Update` siguiente `AddNew`. El búfer de edición no se restaura si se abandona un búfer de edición recién modificado; por ejemplo, se mueve a otro registro antes de llamar a `Update`.

Además de intercambiar datos entre el origen de datos y los miembros de datos de campo del conjunto de registros, RFX administra los parámetros de enlace. Cuando se abre el conjunto de registros, todos los miembros de datos de parámetro se enlazan en el orden de los marcadores de posición "?" en la instrucción SQL que `CRecordset::Open` construcciones. Para obtener más información, vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

El reemplazo de la clase de conjunto de registros de `DoFieldExchange` realiza todo el trabajo, moviendo los datos en ambas direcciones. Al igual que el intercambio de datos de cuadros de diálogo (DDX), RFX necesita información sobre los miembros de datos de la clase. El asistente proporciona la información necesaria escribiendo una implementación específica del conjunto de registros de `DoFieldExchange` automáticamente, en función de los nombres de los miembros de datos de campo y los tipos de datos que se especifiquen con el asistente.

##  <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Proceso de intercambio de campos de registros

En esta sección se describe la secuencia de eventos RFX a medida que se abre un objeto de conjunto de registros y se agregan, actualizan y eliminan registros. La [secuencia de tabla de las operaciones de RFX durante la apertura del conjunto de registros](#_core_sequence_of_rfx_operations_during_recordset_open) y la [secuencia de tabla de las operaciones de RFX durante el desplazamiento](#_core_sequence_of_rfx_operations_during_scrolling) en este tema muestran el proceso a medida que rfx procesa un comando `Move` en el conjunto de registros y a medida que RFX administra una actualización. Durante estos procesos, se llama a [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) para realizar muchas operaciones diferentes. El miembro de datos `m_nOperation` del objeto [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) determina qué operación se solicita. Puede que le resulte útil leer un conjunto de registros [: cómo los conjuntos de registros seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) y [el conjunto de registros: Cómo actualizan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) antes de leer este material.

###  <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX: enlace inicial de columnas y parámetros

Se producen las siguientes actividades de RFX, en el orden mostrado, al llamar a la función miembro [Open](../../mfc/reference/crecordset-class.md#open) de un objeto de conjunto de registros:

- Si el conjunto de registros tiene miembros de datos de parámetros, el marco de trabajo llama `DoFieldExchange` para enlazar los parámetros a marcadores de posición de parámetros en la cadena de instrucción SQL del conjunto de registros. Se utiliza una representación dependiente del tipo de datos del valor del parámetro para cada marcador de posición que se encuentra en la instrucción **Select** . Esto se produce después de preparar la instrucción SQL, pero antes de que se ejecute. Para obtener información sobre la preparación de instrucciones, vea la función `::SQLPrepare` en la *Referencia del programador*de ODBC.

- El marco de trabajo llama `DoFieldExchange` una segunda vez para enlazar los valores de las columnas seleccionadas a los miembros de datos de campo correspondientes en el conjunto de registros. Esto establece el objeto de conjunto de registros como un búfer de edición que contiene las columnas del primer registro.

- El conjunto de registros ejecuta la instrucción SQL y el origen de datos selecciona el primer registro. Las columnas del registro se cargan en los miembros de datos de campo del conjunto de registros.

En la tabla siguiente se muestra la secuencia de operaciones de RFX al abrir un conjunto de registros.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Secuencia de operaciones de RFX durante la apertura del conjunto de registros

|La operación|Operación DoFieldExchange|Operación de base de datos/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Abra el conjunto de registros.|||
||2. crear una instrucción SQL.||
|||3. Envíe el SQL.|
||4. enlazar miembros de datos de parámetro.||
||5. enlace los miembros de datos de campo a las columnas.||
|||6. ODBC realiza el movimiento y rellena los datos.|
||7. Corrija los datos de C++.||

Los conjuntos de registros utilizan la ejecución preparada de ODBC para permitir una rápida consulta con la misma instrucción SQL. Para obtener más información sobre la ejecución preparada, vea la *Referencia del programador* del SDK de ODBC en MSDN Library.

###  <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX: desplazamiento

Al desplazarse de un registro a otro, el marco de trabajo llama a `DoFieldExchange` para reemplazar los valores almacenados previamente en los miembros de datos de campo con valores para el nuevo registro.

En la tabla siguiente se muestra la secuencia de operaciones de RFX cuando el usuario se mueve de un registro a otro.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Secuencia de operaciones de RFX durante el desplazamiento

|La operación|Operación DoFieldExchange|Operación de base de datos/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. llame a `MoveNext` o a una de las otras funciones de movimiento.|||
|||2. ODBC realiza el movimiento y rellena los datos.|
||3. Corrija los datos de C++.||

###  <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: agregar nuevos registros y editar registros existentes

Si agrega un nuevo registro, el conjunto de registros funciona como un búfer de edición para crear el contenido del nuevo registro. Al igual que con la adición de registros, la edición de registros implica cambiar los valores de los miembros de datos de campo del conjunto de registros. Desde la perspectiva de RFX, la secuencia es la siguiente:

1. La llamada a la función miembro [AddNew](../../mfc/reference/crecordset-class.md#addnew) o [Edit](../../mfc/reference/crecordset-class.md#edit) del conjunto de registros hace que RFX almacene el búfer de edición actual para que se pueda restaurar más adelante.

1. `AddNew` o `Edit` prepara los campos en el búfer de edición para que RFX pueda detectar los miembros de datos de campo modificados.

   Dado que un nuevo registro no tiene valores anteriores con los que comparar los nuevos, `AddNew` establece el valor de cada miembro de datos de campo en un valor de PSEUDO_NULL. Más adelante, al llamar a `Update`, RFX compara el valor de cada miembro de datos con el valor de PSEUDO_NULL. Si hay alguna diferencia, se ha establecido el miembro de datos. (PSEUDO_NULL no es lo mismo que una columna de registro con un valor null verdadero ni ninguno de ellos igual que C++ null).

   A diferencia de la llamada `Update` para `AddNew`, la llamada a `Update` para `Edit` compara los valores actualizados con los valores previamente almacenados en lugar de usar PSEUDO_NULL. La diferencia es que `AddNew` no tiene valores previamente almacenados para la comparación.

1. Establezca directamente los valores de los miembros de datos de campo cuyos valores desea editar o que desee rellenar para un nuevo registro. Esto puede incluir la llamada a `SetFieldNull`.

1. La llamada a [Update](../../mfc/reference/crecordset-class.md#update) comprueba los miembros de datos de campo modificados, como se describe en el paso 2 (vea la [secuencia de tabla de las operaciones de RFX durante el desplazamiento](#_core_sequence_of_rfx_operations_during_scrolling)). Si no ha cambiado ninguno, `Update` devuelve 0. Si han cambiado algunos miembros de datos de campo, `Update` prepara y ejecuta una instrucción **Insert** de SQL que contiene los valores de todos los campos actualizados en el registro.

1. Por `AddNew`, `Update` concluye restaurando los valores previamente almacenados del registro que era el actual antes de la llamada a `AddNew`. Por `Edit`, los nuevos valores editados permanecen en su lugar.

En la tabla siguiente se muestra la secuencia de operaciones de RFX al agregar un nuevo registro o editar un registro existente.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Secuencia de operaciones de RFX durante la operación AddNew y Edit

|La operación|Operación DoFieldExchange|Operación de base de datos/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. llame a `AddNew` o `Edit`.|||
||2. Realice una copia de seguridad del búfer de edición.||
||3. por `AddNew`, marque los miembros de datos de campo como "Clean" y null.||
|4. asignar valores a los miembros de datos del campo de conjunto de registros.|||
|5. llame a `Update`.|||
||6. Compruebe los campos modificados.||
||7. cree una instrucción **Insert** de SQL para `AddNew` o instrucción **Update** para `Edit`.||
|||8. Envíe el SQL.|
||9. por `AddNew`, restaure el búfer de edición a su contenido de copia de seguridad. Para `Edit`, elimine la copia de seguridad.||

### <a name="rfx-deleting-existing-records"></a>RFX: eliminar registros existentes

Cuando se elimina un registro, RFX establece todos los campos en NULL como recordatorio de que el registro se ha eliminado y debe quitarlo. No es necesario ninguna otra información de secuencia de RFX.

## <a name="see-also"></a>Consulte también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Consumidor ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Macros, funciones globales y variables globales](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange (clase)](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::D oFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
