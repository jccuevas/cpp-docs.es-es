---
title: "Conjunto de registros: Cómo AddNew, Edit y Delete funcionan (ODBC) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bc26033ff0da5c49ddcb848f648925978f7b53da
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Conjunto de registros: Funcionamiento de AddNew, Edit y Delete (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema se explica cómo el `AddNew`, **editar**, y **eliminar** funciones miembro de clase `CRecordset` de trabajo. Los temas tratados son:  
  
-   [Cómo se agregan registros](#_core_adding_a_record)  
  
-   [Visibilidad de los registros agregados](#_core_visibility_of_added_records)  
  
-   [Cómo funciona la edición de registros](#_core_editing_an_existing_record)  
  
-   [Funcionamiento de la eliminación de registros](#_core_deleting_a_record)  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si se usa la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Como un complemento, debe leer [intercambio de campos de registros: funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), que describe el papel correspondiente de RFX en las operaciones de actualización.  
  
##  <a name="_core_adding_a_record"></a>Agregar un registro  

 Agregar un nuevo registro a un conjunto de registros implica llamar a la función miembro [AddNew](../../mfc/reference/crecordset-class.md#addnew) , establecer los valores de los miembros de datos de campo del nuevo registro y una llamada a función miembro la [actualización](../../mfc/reference/crecordset-class.md#update) función de miembro para escribir el registro para el origen de datos.  
  
 Como condición previa para llamar a `AddNew`, el conjunto de registros debe no se han abierto como de solo lectura. El `CanUpdate` y `CanAppend` funciones miembro permiten determinar estas condiciones.  
  
 Cuando se llama a `AddNew`:  
  
-   Se almacena el registro en el búfer de edición, por lo que su contenido se puede restaurar si se cancela la operación.  
  
-   Por lo que es posible detectar cambios en ellos más adelante, se marcan los miembros de datos de campo. Limpiar (sin modificar) los datos del campo también se marcan los miembros y establecer en un valor Null.  
  
 Después de llamar a `AddNew`, el búfer de edición representa una nueva, Vaciar registro, listo para llenarlo de valores. Para ello, establece manualmente los valores mediante la asignación a ellos. En lugar de especificar un valor de datos real para un campo, puede llamar a `SetFieldNull` para especificar el valor Null.  
  
 Para confirmar sus cambios, se llama a **actualización**. Cuando se llama a **actualización** para el nuevo registro:  
  
-   Si el controlador ODBC admite la **:: SQLSetPos** función de la API de ODBC, MFC usa la función para agregar el registro en el origen de datos. Con **:: SQLSetPos**, MFC puede agregar un registro de forma más eficaz porque no tiene que crear y procesar una instrucción SQL.  
  
-   Si **:: SQLSetPos** no puede ser utilizado, MFC hace lo siguiente:  
  
    1.  Si no se detectan cambios, **actualización** no hace nada y devuelve 0.  
  
    2.  Si hay cambios, **actualización** construye una instancia de SQL **insertar** instrucción. Las columnas representadas por todos los miembros de datos de campo modificados se enumeran en la **insertar** instrucción. Para forzar una columna que debe incluirse, llame a la [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) función miembro:  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  **Actualización** confirma el nuevo registro: la **insertar** instrucción se ejecuta y el registro se confirma en la tabla en el origen de datos (y el conjunto de registros, si no es una instantánea) a menos que una transacción está en curso.  
  
    4.  Se restaura el registro almacenado en el búfer de edición. El registro que era el actual antes de la `AddNew` llamada es actual, sin importar si el **insertar** instrucción se ha ejecutado correctamente.  
  
    > [!TIP]
    >  Para el control completo de un nuevo registro, adopte el siguiente enfoque: establecer los valores de los campos que tienen valores y, a continuación, establezca explícitamente cualquier campo que permanezca como Null mediante una llamada a `SetFieldNull` con un puntero al campo y el parámetro **es TRUE**  (valor predeterminado). Si desea asegurarse de que un campo no se escribe en el origen de datos, llamada `SetFieldDirty` con un puntero al campo y el parámetro **FALSE**y no modifique el valor del campo. Para determinar si un campo puede ser Null, llame a `IsFieldNullable`.  
  
    > [!TIP]
    >  Para detectar si los miembros de datos del conjunto de registros cambian el valor, MFC utiliza un **PSEUDO_NULL** valor adecuado para cada tipo de datos que se puede almacenar en un conjunto de registros. Si se debe establecer explícitamente un campo en el **PSEUDO_NULL** value y el campo parece ya estén marcadas como Null, también debe llamar a `SetFieldNull`, pasa la dirección del campo en el primer parámetro y **FALSE**en el segundo parámetro.  
  
##  <a name="_core_visibility_of_added_records"></a>Visibilidad de los registros agregados  
 ¿Cuándo es visible para el conjunto de registros un registro agregado? Los registros agregados a veces se mostrarán y a veces no están visibles, dependiendo de dos factores:  
  
-   El controlador de qué es capaz de.  
  
-   Lo que el marco de trabajo puede sacar partido de.  
  
 Si el controlador ODBC admite la **:: SQLSetPos** función de la API de ODBC, MFC usa la función para agregar registros. Con **:: SQLSetPos**, registros agregados son visibles para cualquier conjunto de registros MFC actualizable. Sin compatibilidad con la función, agregados no son visibles los registros y se debe llamar a **Requery** para verlos. Usar **:: SQLSetPos** también es más eficaz.  
  
##  <a name="_core_editing_an_existing_record"></a>Editar un registro existente  
 Editar un registro existente en un conjunto de registros implica desplazarse al registro, el conjunto de registros de llamada [editar](../../mfc/reference/crecordset-class.md#edit) , establecer los valores de los miembros de datos de campo del nuevo registro y una llamada a función miembro la [actualizar](../../mfc/reference/crecordset-class.md#update)función de miembro para escribir el registro modificado en el origen de datos.  
  
 Como condición previa para llamar a **editar**, el conjunto de registros debe ser actualizable y hallarse en un registro. El `CanUpdate` y `IsDeleted` funciones miembro permiten determinar estas condiciones. También, el registro actual no puede haber sido eliminado todavía, y debe haber registros en el conjunto de registros (ambos `IsBOF` y `IsEOF` devuelven 0).  
  
 Cuando se llama a **editar**, se almacena el registro en el búfer de edición (el registro actual). Valores del registro almacenado más adelante se utilizan para detectar si los campos han cambiado.  
  
 Después de llamar a **editar**, el búfer de edición continúa representando el registro actual, pero ahora está listo para aceptar los cambios a los miembros de datos de campo. Para cambiar el registro, establecer manualmente los valores de los miembros de datos de campo que desea editar. En lugar de especificar un valor de datos real para un campo, puede llamar a `SetFieldNull` para especificar el valor Null. Para confirmar los cambios, llame a **actualización**.  
  
> [!TIP]
>  Para sacar partido de `AddNew` o **editar** llamada, el modo de **mover** con el parámetro **AFX_MOVE_REFRESH**.  
  
 Como condición previa para llamar a **actualización**, el conjunto de registros no debe estar vacío y no se debe haber eliminado el registro actual. `IsBOF`, `IsEOF`, y `IsDeleted` deben devolver 0.  
  
 Cuando se llama a **actualización** para el registro editado:  
  
-   Si el controlador ODBC admite la **:: SQLSetPos** función de la API de ODBC, MFC usa la función para actualizar el registro en el origen de datos. Con **:: SQLSetPos**, el controlador compara el búfer de edición con el registro correspondiente en el servidor, actualizar el registro en el servidor si los dos son diferentes. Con **:: SQLSetPos**, MFC puede actualizar un registro de forma más eficaz porque no tiene que crear y procesar una instrucción SQL.  
  
     O bien  
  
-   Si **:: SQLSetPos** no puede ser utilizado, MFC hace lo siguiente:  
  
    1.  Si no ha habido ningún cambio, **actualización** no hace nada y devuelve 0.  
  
    2.  Si hay cambios, **actualización** construye una instancia de SQL **actualización** instrucción. Las columnas enumeradas en la **actualización** instrucción se basan en los miembros de datos de campo que han cambiado.  
  
    3.  **Actualización** confirma los cambios, se ejecuta el **actualización** instrucción: y se cambia el registro en el origen de datos, pero no se confirma si hay una transacción está en curso (vea [transacción: realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) para obtener información sobre cómo afecta la transacción a la actualización). ODBC conserva una copia del registro, que también cambia.  
  
    4.  A diferencia del proceso de `AddNew`, **editar** proceso no restaura el registro almacenado. El registro editado permanece en su lugar como el registro actual.  
  
    > [!CAUTION]
    >  Al prepararse para actualizar un conjunto de registros mediante una llamada a **actualizar**, tenga cuidado de que el conjunto de registros incluye todas las columnas que componen la clave principal de la tabla (o todas las columnas de cualquier único índice en la tabla, o suficientes columnas para forma única identificar la fila). En algunos casos, el marco de trabajo sólo puede utilizar las columnas seleccionadas en el conjunto de registros para identificar qué registro de la tabla se actualiza. Sin todas las columnas necesarias, se podrían actualizar varios registros en la tabla. En este caso, el marco de trabajo produce excepciones al llamar a **actualización**.  
  
    > [!TIP]
    >  Si se llama a `AddNew` o **editar** después de haber llamado a cualquier función anteriormente pero antes de llamar a **actualización**, el búfer de edición se actualiza con el registro almacenado, reemplazando el registro nuevo o editado en progreso. Este comportamiento proporciona una forma para anular una `AddNew` o **editar** y comenzar una nueva: si se determina que el registro en proceso presenta error, basta con llamar a **editar** o `AddNew` nuevo.  
  
##  <a name="_core_deleting_a_record"></a>Eliminar un registro  
 Eliminar un registro de un conjunto de registros implica desplazarse al registro y el conjunto de registros de llamada [eliminar](../../mfc/reference/crecordset-class.md#delete) función miembro. A diferencia de `AddNew` y **editar**, **eliminar** no requiere una llamada similar a **actualización**.  
  
 Como condición previa para llamar a **eliminar**, el conjunto de registros debe ser actualizable y debe estar en un registro. El `CanUpdate`, `IsBOF`, `IsEOF`, y `IsDeleted` funciones miembro permiten determinar estas condiciones.  
  
 Cuando se llama a **eliminar**:  
  
-   Si el controlador ODBC admite la **:: SQLSetPos** función de la API de ODBC, MFC usa la función para eliminar el registro en el origen de datos. Usar **:: SQLSetPos** suele ser más eficaz que el uso de SQL.  
  
     O bien  
  
-   Si **:: SQLSetPos** no puede ser utilizado, MFC hace lo siguiente:  
  
    1.  El registro actual en el búfer de edición no se copia como en `AddNew` y **editar**.  
  
    2.  **Eliminar** construye una instancia de SQL **eliminar** instrucción que quita el registro.  
  
         El registro actual en el búfer de edición no se almacena como en `AddNew` y **editar**.  
  
    3.  **Eliminar** confirma la eliminación, se ejecuta el **eliminar** instrucción. El registro se marca como eliminado en el origen de datos y, si el registro es una instantánea, en ODBC.  
  
    4.  Valores del registro eliminado todavía están en los miembros de datos de campo del conjunto de registros, pero se marcan los miembros de datos de campo Null y el conjunto de registros `IsDeleted` función miembro devuelve un valor distinto de cero.  
  
    > [!NOTE]
    >  Después de eliminar un registro, debe desplazarse a otro registro para llenar el búfer de edición con los datos del nuevo registro. Es un error al llamar a **eliminar** nuevo o para llamar a **editar**.  
  
 Para obtener información acerca de las instrucciones SQL usadas en operaciones de actualización, vea [SQL](../../data/odbc/sql.md).  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Más información acerca de las actualizaciones (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)   
 [Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)