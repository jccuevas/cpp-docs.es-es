---
title: 'Conjunto de registros: Funcionamiento de AddNew, Edit y Delete (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
ms.openlocfilehash: 63718a6be3a9ce19ddbce923a84def21448c42a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367002"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Conjunto de registros: Funcionamiento de AddNew, Edit y Delete (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema `AddNew` `Edit`se `Delete` explica cómo `CRecordset` funcionan las funciones , , y miembro de la clase. Temas cubiertos:

- [Cómo funciona la adición de registros](#_core_adding_a_record)

- [Visibilidad de los registros añadidos](#_core_visibility_of_added_records)

- [Cómo funciona la edición de registros](#_core_editing_an_existing_record)

- [Cómo funciona la eliminación de registros](#_core_deleting_a_record)

> [!NOTE]
> Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usa la obtención masiva de filas, vea [Conjunto de registros: obtención de registros en masa (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Como suplemento, es posible que desee leer Intercambio de campos de [registros: Cómo funciona RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), que describe el rol correspondiente de RFX en las operaciones de actualización.

## <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>Adición de un registro

Agregar un nuevo registro a un conjunto de registros implica llamar a la función miembro [AddNew](../../mfc/reference/crecordset-class.md#addnew) del conjunto de registros, establecer los valores de los miembros de datos de campo del nuevo registro y llamar a la [update](../../mfc/reference/crecordset-class.md#update) función miembro para escribir el registro en el origen de datos.

Como condición previa `AddNew`para llamar , el conjunto de registros no debe haberse abierto como de solo lectura. Las `CanUpdate` `CanAppend` funciones miembro y le permiten determinar estas condiciones.

Cuando llame `AddNew`a :

- El registro en el búfer de edición se almacena, por lo que su contenido se puede restaurar si se cancela la operación.

- Los miembros de datos de campo se marcan para que sea posible detectar cambios en ellos más adelante. Los miembros de datos de campo también se marcan como limpios (sin cambios) y se establecen en null.

Después `AddNew`de llamar a , el búfer de edición representa un nuevo registro vacío, listo para rellenarse con valores. Para ello, puede establecer manualmente los valores asignándoles. En lugar de especificar un valor de datos `SetFieldNull` real para un campo, puede llamar para especificar el valor Null.

Para confirmar los cambios, llame a `Update`. Cuando llame `Update` para el nuevo registro:

- Si el controlador `::SQLSetPos` ODBC admite la función de API ODBC, MFC usa la función para agregar el registro en el origen de datos. Con `::SQLSetPos`, MFC puede agregar un registro de forma más eficaz porque no tiene que construir y procesar una instrucción SQL.

- Si `::SQLSetPos` no se puede utilizar, MFC hace lo siguiente:

   1. Si no se `Update` detecta ningún cambio, no hace nada y devuelve 0.

   1. Si hay cambios, `Update` construye una instrucción SQL **INSERT.** Las columnas representadas por todos los miembros de datos de campo sucios se enumeran en la instrucción **INSERT.** Para forzar la entrada de una columna, llame a la [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) función miembro:

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update`confirma el nuevo registro: se ejecuta la instrucción **INSERT** y el registro se confirma en la tabla del origen de datos (y el conjunto de registros, si no una instantánea) a menos que haya una transacción en curso.

   1. El registro almacenado se restaura en el búfer de edición. El registro que era `AddNew` actual antes de la llamada es actual de nuevo, independientemente de si la instrucción **INSERT** se ejecutó correctamente.

   > [!TIP]
   > Para el control completo de un nuevo registro, tome el siguiente enfoque: establezca los valores de los `SetFieldNull` campos que tendrán valores y, a continuación, establezca explícitamente los campos que permanecerán Null llamando con un puntero al campo y el parámetro TRUE (valor predeterminado). Si desea asegurarse de que un campo no `SetFieldDirty` se escribe en el origen de datos, llame con un puntero al campo y el parámetro FALSE y no modifique el valor del campo. Para determinar si un campo puede `IsFieldNullable`ser Null, llame a .

   > [!TIP]
   > Para detectar cuándo los miembros de datos del conjunto de registros cambian el valor, MFC usa un valor de PSEUDO_NULL adecuado para cada tipo de datos que puede almacenar en un conjunto de registros. Si debe establecer explícitamente un campo en el PSEUDO_NULL valor y el campo `SetFieldNull`ya está marcado como Null, también debe llamar a , pasando la dirección del campo en el primer parámetro y FALSE en el segundo parámetro.

## <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>Visibilidad de los registros añadidos

¿Cuándo es visible un registro agregado para el conjunto de registros? Los registros añadidos a veces aparecen y a veces no son visibles, dependiendo de dos cosas:

- De lo que su conductor es capaz de hacer.

- Lo que el marco puede aprovechar.

Si el controlador `::SQLSetPos` ODBC admite la función de API ODBC, MFC usa la función para agregar registros. Con `::SQLSetPos`, los registros agregados son visibles para cualquier conjunto de registros MFC actualizable. Sin compatibilidad con la función, los `Requery` registros agregados no son visibles y debe llamar para verlos. El `::SQLSetPos` uso también es más eficiente.

## <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>Edición de un registro existente

Editar un registro existente en un conjunto de registros implica desplazarse al registro, llamar a la función miembro [Edit](../../mfc/reference/crecordset-class.md#edit) del conjunto de registros, establecer los valores de los miembros de datos de campo del nuevo registro y llamar a la [Update](../../mfc/reference/crecordset-class.md#update) función miembro para escribir el registro modificado en el origen de datos.

Como condición previa `Edit`para llamar , el conjunto de registros debe ser actualizable y en un registro. Las `CanUpdate` `IsDeleted` funciones miembro y le permiten determinar estas condiciones. El registro actual tampoco debe haberse eliminado ya y `IsBOF` debe `IsEOF` haber registros en el conjunto de registros (ambos y devolver 0).

Cuando se `Edit`llama a , se almacena el registro en el búfer de edición (el registro actual). Los valores del registro almacenado se utilizan más adelante para detectar si los campos han cambiado.

Después `Edit`de llamar a , el búfer de edición sigue representando el registro actual, pero ahora está listo para aceptar cambios en los miembros de datos de campo. Para cambiar el registro, establezca manualmente los valores de los miembros de datos de campo que desee editar. En lugar de especificar un valor de datos `SetFieldNull` real para un campo, puede llamar para especificar el valor Null. Para confirmar los `Update`cambios, llame a .

> [!TIP]
> Para salir `AddNew` del `Edit` modo `Move` o, llame con el parámetro *AFX_MOVE_REFRESH*.

Como condición previa `Update`para llamar a , el conjunto de registros no debe estar vacío y el registro actual no debe haberse eliminado. `IsBOF`, `IsEOF`, `IsDeleted` y todos deben devolver 0.

Cuando se `Update` llama para el registro editado:

- Si el controlador `::SQLSetPos` ODBC admite la función de API ODBC, MFC usa la función para actualizar el registro en el origen de datos. Con `::SQLSetPos`, el controlador compara el búfer de edición con el registro correspondiente en el servidor, actualizando el registro en el servidor si los dos son diferentes. Con `::SQLSetPos`, MFC puede actualizar un registro de forma más eficaz porque no tiene que construir y procesar una instrucción SQL.

   \- o -

- Si `::SQLSetPos` no se puede utilizar, MFC hace lo siguiente:

   1. Si no ha habido `Update` cambios, no hace nada y devuelve 0.

   1. Si hay cambios, `Update` construye una instrucción **UPDATE** de SQL. Las columnas enumeradas en la instrucción **UPDATE** se basan en los miembros de datos de campo que han cambiado.

   1. `Update`confirma los cambios (ejecuta la instrucción **UPDATE)** y el registro se cambia en el origen de datos, pero no se confirma si una transacción está en curso (consulte [Transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) para obtener información sobre cómo afecta la transacción a la actualización). ODBC mantiene una copia del registro, que también cambia.

   1. A diferencia `AddNew`del `Edit` proceso para , el proceso no restaura el registro almacenado. El registro editado permanece en su lugar como el registro actual.

   > [!CAUTION]
   > Cuando se prepara para actualizar `Update`un conjunto de registros mediante una llamada, tenga cuidado de que el conjunto de registros incluya todas las columnas que componen la clave principal de la tabla (o todas las columnas de cualquier índice único de la tabla o suficientes columnas para identificar de forma única la fila). En algunos casos, el marco de trabajo sólo puede utilizar las columnas seleccionadas en el conjunto de registros para identificar qué registro de la tabla se actualiza. Sin todas las columnas necesarias, es posible que se actualicen varios registros en la tabla. En este caso, el marco de `Update`trabajo produce excepciones cuando se llama a .

   > [!TIP]
   > Si llama `AddNew` `Edit` o después de haber llamado `Update`a cualquiera de las funciones anteriormente pero antes de llamar , el búfer de edición se actualiza con el registro almacenado, reemplazando el registro nuevo o editado en curso. Este comportamiento le ofrece una `AddNew` `Edit` manera de anular un o y comenzar uno nuevo: si determina `Edit` `AddNew` que el registro en curso es defectuoso, simplemente llame o de nuevo.

## <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>Eliminación de un registro

Eliminar un registro de un conjunto de registros implica desplazarse al registro y llamar a la función miembro [Delete](../../mfc/reference/crecordset-class.md#delete) del conjunto de registros. A `AddNew` `Edit`diferencia `Delete` de y , `Update`no requiere una llamada coincidente a .

Como condición previa `Delete`para llamar , el conjunto de registros debe ser actualizable y debe estar en un registro. Las `CanUpdate` `IsBOF`funciones miembro , , `IsEOF`, y `IsDeleted` permiten determinar estas condiciones.

Cuando llame `Delete`a :

- Si el controlador `::SQLSetPos` ODBC admite la función de API ODBC, MFC usa la función para eliminar el registro en el origen de datos. El `::SQLSetPos` uso suele ser más eficaz que el uso de SQL.

   \- o -

- Si `::SQLSetPos` no se puede utilizar, MFC hace lo siguiente:

   1. El registro actual en el búfer de `AddNew` edición no se realiza una copia de seguridad como en y `Edit`.

   1. `Delete`construye una instrucción **DELETE** de SQL que quita el registro.

      El registro actual en el búfer `AddNew` de `Edit`edición no se almacena como en y .

   1. `Delete`confirma la eliminación: ejecuta la instrucción **DELETE.** El registro se marca como eliminado en el origen de datos y, si el registro es una instantánea, en ODBC.

   1. Los valores del registro eliminado siguen estando en los miembros de datos de campo `IsDeleted` del conjunto de registros, pero los miembros de datos de campo se marcan como Null y la función miembro del conjunto de registros devuelve un valor distinto de cero.

   > [!NOTE]
   > Después de eliminar un registro, debe desplazarse a otro registro para rellenar el búfer de edición con los datos del nuevo registro. Es un error `Delete` llamar de `Edit`nuevo o llamar a .

Para obtener información acerca de las instrucciones SQL utilizadas en las operaciones de actualización, vea [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Información adicional sobre las actualizaciones (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)
