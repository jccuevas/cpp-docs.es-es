---
title: 'Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- records [C++], deleting
- AddNew method
- ODBC recordsets [C++], deleting records
- data in recordsets [C++]
- record editing [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: af3a3eb08ce5749c0cfe5ca2d1f59213826ff7ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
> [!NOTE]
>  Ahora se pueden agregar registros de forma masiva con mayor eficiencia. Para obtener más información, consulte [conjunto de registros: agregar registros de forma masiva (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si se usa la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Los conjuntos de registros dinámicos y as instantáneas actualizables permiten agregar, editar (actualizar) y eliminar registros. En este tema se explica:  
  
-   [Cómo determinar si el conjunto de registros es actualizable](#_core_determining_whether_your_recordset_is_updatable).  
  
-   [Cómo agregar un nuevo registro](#_core_adding_a_record_to_a_recordset).  
  
-   [Cómo editar un registro existente](#_core_editing_a_record_in_a_recordset).  
  
-   [Cómo eliminar un registro](#_core_deleting_a_record_from_a_recordset).  
  
 Para obtener más información sobre cómo se realizan las actualizaciones y cómo aparecen las actualizaciones a otros usuarios, vea [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Normalmente, al agregar, editar o eliminar un registro, el conjunto de registros cambia el origen de datos inmediatamente. En su lugar, se pueden agrupar las actualizaciones relacionadas en transacciones. Si hay una transacción en progreso, la actualización no es final hasta que se confirma la transacción. Esto permite recuperar o revertir los cambios. Para obtener información acerca de las transacciones, vea [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
 La siguiente tabla resume las opciones disponibles para conjuntos de registros con diferentes características de actualización.  
  
### <a name="recordset-readupdate-options"></a>Opciones de lectura y actualización de un conjunto de registros  
  
|Tipo|Leer|Edición de registro|Eliminación de registro|Adición de nuevos registros (anexar)|  
|----------|----------|-----------------|-------------------|------------------------|  
|De sólo lectura|Y|N|N|N|  
|Sólo anexar|Y|N|N|Y|  
|Totalmente actualizable|Y|Y|Y|Y|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> Determinar si un conjunto de registros es actualizable  
 Un objeto de conjunto de registros es actualizable si el origen de datos lo es y se abre el conjunto de registros como actualizable. Su capacidad de actualización depende también de la instrucción SQL utilizada, de la funcionalidad del controlador ODBC y de si la biblioteca de cursores ODBC está o no en memoria. No se puede actualizar un conjunto de registros u origen de datos de sólo lectura.  
  
#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Para determinar si el conjunto de registros es actualizable  
  
1.  Llamar al objeto de conjunto de registros [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) función miembro.  
  
     `CanUpdate` devuelve un valor distinto de cero si el conjunto de registros es actualizable.  
  
 De forma predeterminada, los conjuntos de registros son totalmente actualizables (se pueden realizar `AddNew`, **editar**, y **eliminar** operaciones). Pero también puede utilizar el [appendOnly](../../mfc/reference/crecordset-class.md#open) opción para abrir conjuntos de registros actualizables. Un conjunto de registros abierto de esta forma sólo permite agregar nuevos registros con `AddNew`. No se pueden editar ni eliminar registros existentes. Puede probar si un conjunto de registros está abierto solo para anexar llamando a la [CanAppend](../../mfc/reference/crecordset-class.md#canappend) función miembro. `CanAppend` devuelve un valor distinto de cero si el conjunto de registros es totalmente actualizable o si está abierto solo para anexar.  
  
 El código siguiente muestra cómo se puede usar `CanUpdate` para un objeto de conjunto de registros denominado `rsStudentSet`:  
  
```  
if( !rsStudentSet.Open( ) )  
    return FALSE;  
if( !rsStudentSet.CanUpdate( ) )  
{  
    AfxMessageBox( "Unable to update the Student recordset." );  
    return;  
}  
```  
  
> [!CAUTION]
>  Al prepararse para actualizar un conjunto de registros mediante una llamada a **actualizar**, tenga cuidado de que el conjunto de registros incluye todas las columnas que componen la clave principal de la tabla (o todas las columnas de un índice único en la tabla). En algunos casos, el marco de trabajo sólo puede utilizar las columnas seleccionadas en el conjunto de registros para identificar qué registro de la tabla se actualiza. Sin todas las columnas necesarias, se podrían actualizar varios registros de la tabla, dañando posiblemente la integridad referencial de ésta. En este caso, el marco de trabajo produce excepciones al llamar a **actualización**.  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a> Agregar un registro a un conjunto de registros  
 Puede agregar nuevos registros a un conjunto de registros si su [CanAppend](../../mfc/reference/crecordset-class.md#canappend) función miembro devuelve un valor distinto de cero.  
  
#### <a name="to-add-a-new-record-to-a-recordset"></a>Para agregar un nuevo registro a un conjunto de registros  
  
1.  Asegúrese de que el conjunto de registros es actualizable.  
  
2.  Llamar al objeto de conjunto de registros [AddNew](../../mfc/reference/crecordset-class.md#addnew) función miembro.  
  
     `AddNew` prepara el conjunto de registros para que actúe como búfer de edición. Todos los miembros de datos de campo se establecen en el valor especial Null y se marcan como sin cambios, por lo que solo modificados se escriben valores al origen de datos cuando se llama a [actualización](../../mfc/reference/crecordset-class.md#update).  
  
3.  Establezca los valores de los miembros de datos de campo del nuevo registro.  
  
     Asigne valores a los miembros de datos de campo. Aquellos que queden sin asignar no se escriben en el origen de datos.  
  
4.  Llamar al objeto de conjunto de registros **actualización** función miembro.  
  
     **Actualización** completa la adición escribiendo el nuevo registro en el origen de datos. Para obtener información sobre lo que ocurre si no se llama a **actualización**, consulte [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Para obtener información acerca de cómo se agregan registros y cuando los registros agregados son visibles en el conjunto de registros, vea [conjunto de registros: cómo AddNew, Edit y Delete trabajo (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).  
  
 El siguiente ejemplo muestra cómo agregar un nuevo registro:  
  
```  
if( !rsStudent.Open( ) )  
    return FALSE;  
if( !rsStudent.CanAppend( ) )  
    return FALSE;                      // no field values were set  
rsStudent.AddNew( );  
rsStudent.m_strName = strName;  
rsStudent.m_strCity = strCity;  
rsStudent.m_strStreet = strStreet;  
if( !rsStudent.Update( ) )  
{  
    AfxMessageBox( "Record not added; no field values were set." );  
    return FALSE;  
}  
```  
  
> [!TIP]
>  Para cancelar un `AddNew` o **editar** llamar, basta con realizar otra llamada a `AddNew` o **editar** o llamar a **mover** con el **AFX_MOVE_REFRESH**  parámetro. Miembros de datos se restablecen los valores anteriores y todavía está en **editar** o **agregar** modo.  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a> Editar un registro en un conjunto de registros  
 Puede editar los registros existentes si el conjunto de registros [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) función miembro devuelve un valor distinto de cero.  
  
#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Para editar un registro existente en un conjunto de registros  
  
1.  Asegúrese de que el conjunto de registros es actualizable.  
  
2.  Desplácese al registro que desea actualizar.  
  
3.  Llamar al objeto de conjunto de registros [editar](../../mfc/reference/crecordset-class.md#edit) función miembro.  
  
     **Editar** prepara el conjunto de registros para que actúe como búfer de edición. Todos los miembros de datos de campo se marcan para que el conjunto de registros pueda detectar posteriormente si se modificaron. Los nuevos valores de los miembros de datos de campo modificados se escriben en el origen de datos cuando se llama a [actualización](../../mfc/reference/crecordset-class.md#update).  
  
4.  Establezca los valores de los miembros de datos de campo del nuevo registro.  
  
     Asigne valores a los miembros de datos de campo. A los que no asigne valores, permanecen sin modificar.  
  
5.  Llamar al objeto de conjunto de registros **actualización** función miembro.  
  
     **Actualización** completa la acción de editar escribiendo el registro modificado en el origen de datos. Para obtener información sobre lo que ocurre si no se llama a **actualización**, consulte [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Después de editar un registro, éste continúa siendo el registro actual.  
  
 El ejemplo siguiente muestra un **editar** operación. Se supone que el usuario se desplazó a un registro que desea editar.  
  
```  
rsStudent.Edit( );  
rsStudent.m_strStreet = strNewStreet;  
rsStudent.m_strCity = strNewCity;  
rsStudent.m_strState = strNewState;  
rsStudent.m_strPostalCode = strNewPostalCode;  
if( !rsStudent.Update( ) )  
{  
    AfxMessageBox( "Record not updated; no field values were set." );  
    return FALSE;  
}  
```  
  
> [!TIP]
>  Para cancelar un `AddNew` o **editar** llamar, basta con realizar otra llamada a `AddNew` o **editar** o llamar a **mover** con el **AFX_MOVE_REFRESH**  parámetro. Miembros de datos se restablecen los valores anteriores y todavía está en **editar** o **agregar** modo.  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a> Eliminar un registro de un conjunto de registros  
 Puede eliminar registros si el conjunto de registros [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) función miembro devuelve un valor distinto de cero.  
  
#### <a name="to-delete-a-record"></a>Para eliminar un registro  
  
1.  Asegúrese de que el conjunto de registros es actualizable.  
  
2.  Desplácese al registro que desea actualizar.  
  
3.  Llamar al objeto de conjunto de registros [eliminar](../../mfc/reference/crecordset-class.md#delete) función miembro.  
  
     **Eliminar** marca inmediatamente el registro como eliminado tanto en el conjunto de registros en el origen de datos.  
  
     A diferencia de `AddNew` y **editar**, **eliminar** no tiene ningún correspondiente **actualización** llamar.  
  
4.  Desplácese a otro registro.  
  
    > [!NOTE]
    >  Al desplazarse por un conjunto de registros, es posible que no se omitan los registros eliminados. Para obtener más información, consulte el [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) función miembro.  
  
 El ejemplo siguiente muestra un **eliminar** operación. Se supone que el usuario se desplazó a un registro que desea eliminar. Después de **eliminar** es llama, es importante mover a un nuevo registro.  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
 Para obtener más información acerca de los efectos de la `AddNew`, **editar**, y **eliminar** funciones miembro, vea [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)