---
title: 'Conjunto de registros: Cómo AddNew, Edit y Delete (ODBC) de trabajo'
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
ms.openlocfilehash: e5fc6ad2a1fe00367cd8a0b1c53ac914b95018ab
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033214"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Conjunto de registros: Cómo AddNew, Edit y Delete (ODBC) de trabajo

Este tema es aplicable a las clases ODBC de MFC.

Este tema se explica cómo el `AddNew`, `Edit`, y `Delete` funciones miembro de clase `CRecordset` funcione. Los temas tratados se incluyen:

- [Cómo se agregan registros](#_core_adding_a_record)

- [Visibilidad de los registros agregados](#_core_visibility_of_added_records)

- [Cómo funciona la edición de registros](#_core_editing_an_existing_record)

- [Funcionamiento de la eliminación de registros](#_core_deleting_a_record)

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usas la obtención masiva de filas, vea [conjunto de registros: Obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Como complemento, es posible que desee leer [intercambio de campos de registro: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), que describe la función correspondiente de RFX en las operaciones de actualización.

##  <a name="_core_adding_a_record"></a> Adición de un registro

Agregar un nuevo registro a un conjunto de registros implica llamar a la función miembro [AddNew](../../mfc/reference/crecordset-class.md#addnew) , establecer los valores de los miembros de datos de campo del nuevo registro y una llamada a función miembro el [actualización](../../mfc/reference/crecordset-class.md#update) función miembro para escribir el registro al origen de datos.

Como condición previa para llamar a `AddNew`, el conjunto de registros debe no haber abierto como de solo lectura. El `CanUpdate` y `CanAppend` funciones miembro permiten determinar estas condiciones.

Cuando se llama a `AddNew`:

- Se almacena el registro en el búfer de edición, por lo que se pueda restaurar su contenido si se cancela la operación.

- Por lo que es posible detectar cambios en ellos más adelante, se marcan los miembros de datos de campo. Los datos del campo también se marcan como limpio (sin cambios) y se establece en un valor Null.

Después de llamar a `AddNew`, el búfer de edición representa una nueva, Vaciar registro, está preparado para rellenar con valores. Para ello, establece manualmente los valores mediante la asignación a ellos. En lugar de especificar un valor de datos real para un campo, puede llamar a `SetFieldNull` para especificar el valor Null.

Para confirmar sus cambios, se llama a `Update`. Cuando se llama a `Update` para el nuevo registro:

- Si el controlador ODBC admite la `::SQLSetPos` función de la API de ODBC, MFC usa la función para agregar el registro del origen de datos. Con `::SQLSetPos`, MFC puede agregar un registro de forma más eficaz porque no tiene que crear y procesar una instrucción SQL.

- Si `::SQLSetPos` no puede ser utilizado, MFC hace lo siguiente:

   1. Si no se detectan cambios, `Update` no hace nada y devuelve 0.

   1. Si hay cambios, `Update` construye una instancia de SQL **insertar** instrucción. Las columnas representadas por todos los miembros de datos de campos modificados se muestran en el **insertar** instrucción. Para forzar una columna que se incluya, llamar a la [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) función miembro:

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` Confirma el nuevo registro, el **insertar** instrucción se ejecuta y el registro se confirma en la tabla en el origen de datos (y el conjunto de registros, si no es una instantánea) a menos que una transacción está en curso.

   1. Se restaura el registro almacenado en el búfer de edición. El registro que era el actual antes del `AddNew` llamada es actual, sin importar si el **insertar** instrucción se ha ejecutado correctamente.

   > [!TIP]
   > Para un control completo de un nuevo registro, adopte el siguiente enfoque: establecer los valores de los campos que tienen valores y, a continuación, establezca explícitamente los campos que seguirá siendo Null mediante una llamada a `SetFieldNull` con un puntero al campo y el parámetro TRUE (valor predeterminado). Si desea asegurarse de que un campo no se escribe en el origen de datos llamada `SetFieldDirty` con un puntero al campo y el parámetro FALSE y no modifique el valor del campo. Para determinar si un campo puede ser Null, llame a `IsFieldNullable`.

   > [!TIP]
   > Para detectar si los miembros de datos del conjunto de registros cambian el valor, MFC utiliza un valor PSEUDO_NULL apropiado para cada tipo de datos que se puede almacenar en un conjunto de registros. Si debe establecer explícitamente un campo en el valor PSEUDO_NULL y el campo resulta ya estén marcadas como Null, también debe llamar a `SetFieldNull`, pasando la dirección del campo en el primer parámetro y FALSE en el segundo parámetro.

##  <a name="_core_visibility_of_added_records"></a> Visibilidad de los registros agregados

¿Cuándo es visible para el conjunto de registros un registro agregado? Los registros agregados se muestran a veces y a veces no son visibles, dependiendo de dos factores:

- Es capaz de controlador.

- Lo que el marco de trabajo puede aprovechar.

Si el controlador ODBC admite la `::SQLSetPos` función de la API de ODBC, MFC usa la función para agregar registros. Con `::SQLSetPos`, registros agregados son visibles para cualquier conjunto de registros actualizable de MFC. Sin compatibilidad con la función, agregados no son visibles los registros y debe llamar a `Requery` para verlos. Mediante `::SQLSetPos` también es más eficaz.

##  <a name="_core_editing_an_existing_record"></a> Editar un registro existente

Editar un registro existente en un conjunto de registros implica desplazarse al registro, una llamada a la función miembro [editar](../../mfc/reference/crecordset-class.md#edit) , establecer los valores de los miembros de datos de campo del nuevo registro y una llamada a función miembro el [actualizar](../../mfc/reference/crecordset-class.md#update)función miembro para escribir el registro modificado en el origen de datos.

Como condición previa para llamar a `Edit`, el conjunto de registros debe ser actualizable y en un registro. El `CanUpdate` y `IsDeleted` funciones miembro permiten determinar estas condiciones. También, el registro actual no puede que se ha eliminado ya y debe haber registros en el conjunto de registros (ambos `IsBOF` y `IsEOF` devuelven 0).

Cuando se llama a `Edit`, se almacena el registro en el búfer de edición (el registro actual). Valores del registro almacenado más adelante se utilizan para detectar si han cambiado los campos.

Después de llamar a `Edit`, el búfer de edición todavía representa el registro actual, pero ahora está listo para aceptar los cambios a los miembros de datos de campo. Para cambiar el registro, establecer manualmente los valores de miembros de datos de campo que desea editar. En lugar de especificar un valor de datos real para un campo, puede llamar a `SetFieldNull` para especificar el valor Null. Para confirmar los cambios, llame a `Update`.

> [!TIP]
> Para sacar de `AddNew` o `Edit` modo, llamada `Move` con el parámetro *AFX_MOVE_REFRESH*.

Como condición previa para llamar a `Update`, el conjunto de registros no debe estar vacío y no se debe haber eliminado el registro actual. `IsBOF`, `IsEOF`, y `IsDeleted` deben devolver 0.

Cuando se llama a `Update` para el registro modificado:

- Si el controlador ODBC admite la `::SQLSetPos` función de la API de ODBC, MFC usa la función para actualizar el registro en el origen de datos. Con `::SQLSetPos`, el controlador compara el búfer de edición con el registro correspondiente en el servidor, actualizando el registro en el servidor si los dos son diferentes. Con `::SQLSetPos`, MFC puede actualizar un registro de forma más eficaz porque no tiene que crear y procesar una instrucción SQL.

   \- o -

- Si `::SQLSetPos` no puede ser utilizado, MFC hace lo siguiente:

   1. Si no ha habido ningún cambio, `Update` no hace nada y devuelve 0.

   1. Si hay cambios, `Update` construye una instancia de SQL **actualización** instrucción. Las columnas enumeradas en la **actualización** instrucción se basan en los miembros de datos de campo que han cambiado.

   1. `Update` Confirma los cambios, ejecuta el **actualización** instrucción y se modifica el registro en el origen de datos, pero no se confirma si hay una transacción está en curso (consulte [transacciones: Realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) para obtener información sobre cómo afecta la transacción a la actualización). ODBC conserva una copia del registro, que también cambia.

   1. A diferencia del proceso `AddNew`, el `Edit` proceso no restaura el registro almacenado. El registro modificado se mantiene como el registro actual.

   > [!CAUTION]
   > Al prepararse para actualizar un conjunto de registros mediante una llamada `Update`, asegúrese de que incluye todas las columnas que componen la clave principal de la tabla (o todas las columnas de un índice único en la tabla, o suficientes columnas para identificar de forma exclusiva la fila). En algunos casos, el marco de trabajo sólo puede utilizar las columnas seleccionadas en el conjunto de registros para identificar qué registro de la tabla se actualiza. Sin todas las columnas necesarias, se podrían actualizar varios registros en la tabla. En este caso, el marco de trabajo produce excepciones al llamar a `Update`.

   > [!TIP]
   > Si se llama a `AddNew` o `Edit` después de haber llamado a cualquier función anteriormente pero antes de llamar a `Update`, el búfer de edición se actualiza con el registro almacenado, reemplazando el registro nuevo o editado en curso. Este comportamiento proporciona una manera de anular un `AddNew` o `Edit` y comenzar una nueva: si determina que el registro en curso es erróneo, basta con llamar a `Edit` o `AddNew` nuevo.

##  <a name="_core_deleting_a_record"></a> Eliminar un registro

Eliminar un registro de un conjunto de registros implica desplazarse al registro y llamar al conjunto de registros [eliminar](../../mfc/reference/crecordset-class.md#delete) función miembro. A diferencia de `AddNew` y `Edit`, `Delete` no requiere una llamada coincidente a `Update`.

Como condición previa para llamar a `Delete`, el conjunto de registros debe ser actualizable y debe estar en un registro. El `CanUpdate`, `IsBOF`, `IsEOF`, y `IsDeleted` funciones miembro permiten determinar estas condiciones.

Cuando se llama a `Delete`:

- Si el controlador ODBC admite la `::SQLSetPos` función de la API de ODBC, MFC usa la función para eliminar el registro en el origen de datos. Uso de `::SQLSetPos` suele ser más eficaz que el uso de SQL.

   \- o -

- Si `::SQLSetPos` no puede ser utilizado, MFC hace lo siguiente:

   1. El registro actual en el búfer de edición no se copia como en `AddNew` y `Edit`.

   1. `Delete` Construye una instancia de SQL **eliminar** instrucción que quita el registro.

      El registro actual en el búfer de edición no se almacena como en `AddNew` y `Edit`.

   1. `Delete` Confirma la eliminación, se ejecuta el **eliminar** instrucción. El registro se marcan como eliminado en el origen de datos y, si el registro es una instantánea en ODBC.

   1. Valores del registro eliminado todavía están en los miembros de datos de campo del conjunto de registros, pero se marcan los miembros de datos de campo Null y el conjunto de registros `IsDeleted` función miembro devuelve un valor distinto de cero.

   > [!NOTE]
   > Después de eliminar un registro, debe desplazarse a otro registro para llenar el búfer de edición con los nuevos datos del registro. Es un error llamar a `Delete` nuevo o para llamar a `Edit`.

Para obtener información acerca de las instrucciones SQL usadas en las operaciones de actualización, vea [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Más información acerca de las actualizaciones (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)