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
ms.openlocfilehash: 8799ac36c443898f1e32b539f017e682bbf3e033
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212917"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Conjunto de registros: Funcionamiento de AddNew, Edit y Delete (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo funcionan las funciones miembro de `AddNew`, `Edit`y `Delete` de la clase `CRecordset`. Temas cubiertos:

- [Cómo funciona la adición de registros](#_core_adding_a_record)

- [Visibilidad de los registros agregados](#_core_visibility_of_added_records)

- [Cómo funcionan los registros de edición](#_core_editing_an_existing_record)

- [Cómo funciona la eliminación de registros](#_core_deleting_a_record)

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usa la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Como complemento, puede que desee leer el [intercambio de campos de registros:](../../data/odbc/record-field-exchange-how-rfx-works.md)funcionamiento de RFX, que describe el rol correspondiente de RFX en las operaciones de actualización.

##  <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>Agregar un registro

Agregar un nuevo registro a un conjunto de registros implica llamar a la función miembro [AddNew](../../mfc/reference/crecordset-class.md#addnew) del conjunto de registros, establecer los valores de los miembros de datos de campo del nuevo registro y llamar a la función miembro [Update](../../mfc/reference/crecordset-class.md#update) para escribir el registro en el origen de datos.

Como condición previa para llamar a `AddNew`, el conjunto de registros no debe haberse abierto como de solo lectura. Las funciones miembro `CanUpdate` y `CanAppend` permiten determinar estas condiciones.

Cuando se llama a `AddNew`:

- Se almacena el registro en el búfer de edición, por lo que su contenido se puede restaurar si se cancela la operación.

- Los miembros de datos de campo se marcan para que sea posible detectar los cambios en ellos más adelante. Los miembros de datos de campo también se marcan como limpios (sin cambios) y se establecen en un valor null.

Después de llamar a `AddNew`, el búfer de edición representa un nuevo registro vacío, listo para rellenarse con valores. Para ello, establezca los valores manualmente mediante la asignación a ellos. En lugar de especificar un valor de datos real para un campo, puede llamar a `SetFieldNull` para especificar el valor null.

Para confirmar los cambios, llame a `Update`. Cuando llame a `Update` para el nuevo registro:

- Si el controlador ODBC admite la función de la API de ODBC `::SQLSetPos`, MFC utiliza la función para agregar el registro en el origen de datos. Con `::SQLSetPos`, MFC puede Agregar un registro de forma más eficaz, ya que no tiene que crear y procesar una instrucción SQL.

- Si no se puede usar `::SQLSetPos`, MFC hace lo siguiente:

   1. Si no se detecta ningún cambio, `Update` no realiza ninguna acción y devuelve 0.

   1. Si hay cambios, `Update` crea una instrucción **Insert** de SQL. Las columnas representadas por todos los miembros de datos de campos modificados se enumeran en la instrucción **Insert** . Para forzar la inclusión de una columna, llame a la función miembro [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) :

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` confirma el nuevo registro: se ejecuta la instrucción **Insert** y el registro se confirma en la tabla del origen de datos (y en el conjunto de registros, si no es una instantánea) a menos que haya una transacción en curso.

   1. El registro almacenado se restaura en el búfer de edición. El registro que era el actual antes de la llamada a `AddNew` vuelve a estar vigente con independencia de si la instrucción **Insert** se ejecutó correctamente.

   > [!TIP]
   > Para tener un control completo de un nuevo registro, adopte el siguiente enfoque: establezca los valores de los campos que tendrán valores y, a continuación, establezca explícitamente los campos que seguirán siendo Null llamando a `SetFieldNull` con un puntero al campo y el parámetro TRUE (valor predeterminado). Si desea asegurarse de que un campo no se escribe en el origen de datos, llame a `SetFieldDirty` con un puntero al campo y el parámetro FALSE, y no modifique el valor del campo. Para determinar si un campo puede ser null, llame a `IsFieldNullable`.

   > [!TIP]
   > Para detectar si los miembros de datos del conjunto de registros cambian de valor, MFC utiliza un valor PSEUDO_NULL apropiado para cada tipo de datos que se puede almacenar en un conjunto de registros. Si debe establecer explícitamente un campo en el valor PSEUDO_NULL y el campo ya tiene que estar marcado como null, también debe llamar a `SetFieldNull`, pasar la dirección del campo en el primer parámetro y FALSE en el segundo parámetro.

##  <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>Visibilidad de los registros agregados

¿Cuándo se puede ver un registro agregado en el conjunto de registros? Los registros agregados a veces aparecen y, en ocasiones, no son visibles, en función de dos cosas:

- Qué es capaz de su controlador.

- Lo que el marco de trabajo puede aprovechar.

Si el controlador ODBC admite la función de la API de ODBC `::SQLSetPos`, MFC utiliza la función para agregar registros. Con `::SQLSetPos`, los registros agregados son visibles para cualquier conjunto de registros MFC actualizable. Sin compatibilidad con la función, los registros agregados no son visibles y debe llamar a `Requery` para verlos. El uso de `::SQLSetPos` también es más eficaz.

##  <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>Editar un registro existente

Editar un registro existente en un conjunto de registros implica desplazarse al registro, llamar a la función miembro [Edit](../../mfc/reference/crecordset-class.md#edit) del conjunto de registros, establecer los valores de los miembros de datos de campo del nuevo registro y llamar a la función miembro [Update](../../mfc/reference/crecordset-class.md#update) para escribir el registro cambiado en el origen de datos.

Como condición previa para llamar a `Edit`, el conjunto de registros debe ser actualizable y en un registro. Las funciones miembro `CanUpdate` y `IsDeleted` permiten determinar estas condiciones. El registro actual tampoco se debe haber eliminado y debe haber registros en el conjunto de registros (tanto `IsBOF` como `IsEOF` devuelven 0).

Cuando se llama a `Edit`, se almacena el registro del búfer de edición (el registro actual). Los valores del registro almacenado se utilizan posteriormente para detectar si han cambiado los campos.

Después de llamar a `Edit`, el búfer de edición todavía representa el registro actual, pero ahora está listo para aceptar los cambios en los miembros de datos de campo. Para cambiar el registro, establezca manualmente los valores de los miembros de datos de campo que desee editar. En lugar de especificar un valor de datos real para un campo, puede llamar a `SetFieldNull` para especificar el valor null. Para confirmar los cambios, llame a `Update`.

> [!TIP]
> Para salir del modo de `AddNew` o `Edit`, llame a `Move` con el parámetro *AFX_MOVE_REFRESH*.

Como condición previa para llamar a `Update`, el conjunto de registros no debe estar vacío y no se debe haber eliminado el registro actual. `IsBOF`, `IsEOF`y `IsDeleted` deben devolver 0.

Cuando llame a `Update` para el registro editado:

- Si el controlador ODBC admite la función de la API de ODBC `::SQLSetPos`, MFC utiliza la función para actualizar el registro en el origen de datos. Con `::SQLSetPos`, el controlador compara el búfer de edición con el registro correspondiente en el servidor, actualizando el registro en el servidor si los dos son diferentes. Con `::SQLSetPos`, MFC puede actualizar un registro de forma más eficaz, ya que no tiene que crear y procesar una instrucción SQL.

   \- O bien

- Si no se puede usar `::SQLSetPos`, MFC hace lo siguiente:

   1. Si no se ha producido ningún cambio, `Update` no realiza ninguna acción y devuelve 0.

   1. Si hay cambios, `Update` crea una instrucción **Update** de SQL. Las columnas enumeradas en la instrucción **Update** se basan en los miembros de datos de campo que han cambiado.

   1. `Update` confirma los cambios (ejecuta la instrucción **Update** ) y el registro se cambia en el origen de datos, pero no se confirma si una transacción está en curso (vea [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) para obtener información sobre cómo afecta la transacción a la actualización). ODBC mantiene una copia del registro, que también cambia.

   1. A diferencia del proceso de `AddNew`, el proceso de `Edit` no restaura el registro almacenado. El registro editado permanece en su lugar como registro actual.

   > [!CAUTION]
   > Cuando prepare la actualización de un conjunto de registros mediante una llamada a `Update`, tenga cuidado de que el conjunto de registros incluya todas las columnas que conforman la clave principal de la tabla (o todas las columnas de cualquier índice único en la tabla, o suficientes columnas para identificar la fila de forma única). En algunos casos, el marco de trabajo sólo puede utilizar las columnas seleccionadas en el conjunto de registros para identificar qué registro de la tabla se actualiza. Sin todas las columnas necesarias, es posible que se actualicen varios registros en la tabla. En este caso, el marco de trabajo produce excepciones cuando se llama a `Update`.

   > [!TIP]
   > Si llama a `AddNew` o `Edit` después de llamar a una función anteriormente, pero antes de llamar a `Update`, el búfer de edición se actualiza con el registro almacenado, reemplazando el registro nuevo o editado en curso. Este comportamiento le permite anular un `AddNew` o `Edit` y comenzar uno nuevo: si determina que el registro en curso es erróneo, simplemente llame a `Edit` o a `AddNew` de nuevo.

##  <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>Eliminar un registro

Eliminar un registro de un conjunto de registros implica desplazarse al registro y llamar a la función miembro [Delete](../../mfc/reference/crecordset-class.md#delete) del conjunto de registros. A diferencia de `AddNew` y `Edit`, `Delete` no requiere una llamada coincidente a `Update`.

Como condición previa para llamar a `Delete`, el conjunto de registros debe ser actualizable y debe estar en un registro. Las funciones miembro `CanUpdate`, `IsBOF`, `IsEOF`y `IsDeleted` permiten determinar estas condiciones.

Cuando se llama a `Delete`:

- Si el controlador ODBC admite la función de la API de ODBC `::SQLSetPos`, MFC utiliza la función para eliminar el registro del origen de datos. El uso de `::SQLSetPos` suele ser más eficaz que usar SQL.

   \- O bien

- Si no se puede usar `::SQLSetPos`, MFC hace lo siguiente:

   1. No se realiza una copia de seguridad del registro actual en el búfer de edición como en `AddNew` y `Edit`.

   1. `Delete` crea una instrucción **Delete** de SQL que quita el registro.

      El registro actual del búfer de edición no se almacena como en `AddNew` y `Edit`.

   1. `Delete` confirma la eliminación: ejecuta la instrucción **Delete** . El registro se marca como eliminado en el origen de datos y, si el registro es una instantánea, en ODBC.

   1. Los valores del registro eliminado todavía están en los miembros de datos de campo del conjunto de registros, pero los miembros de datos de campo se marcan como NULL y la función miembro `IsDeleted` del conjunto de registros devuelve un valor distinto de cero.

   > [!NOTE]
   > Después de eliminar un registro, debe desplazarse a otro registro para rellenar el búfer de edición con los datos del nuevo registro. Es un error llamar a `Delete` de nuevo o llamar a `Edit`.

Para obtener información sobre las instrucciones SQL que se usan en las operaciones de actualización, vea [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Información adicional sobre las actualizaciones (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)
