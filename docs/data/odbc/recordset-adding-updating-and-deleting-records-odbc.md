---
title: 'Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)'
ms.date: 11/04/2016
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
ms.openlocfilehash: 628ffb2feee385a4114b0dbea074f81678c529d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367110"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

> [!NOTE]
> Ahora se pueden agregar registros de forma masiva con mayor eficiencia. Para obtener más información, vea [Conjunto de registros: agregar registros en masa (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).

> [!NOTE]
> Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usa la obtención masiva de filas, vea [Conjunto de registros: obtención de registros en masa (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Los conjuntos de registros dinámicos y as instantáneas actualizables permiten agregar, editar (actualizar) y eliminar registros. En este tema se explica:

- Cómo determinar si el conjunto de [registros es actualizable.](#_core_determining_whether_your_recordset_is_updatable)

- [Cómo agregar un nuevo registro](#_core_adding_a_record_to_a_recordset).

- [Cómo editar un registro existente.](#_core_editing_a_record_in_a_recordset)

- [Cómo eliminar un registro](#_core_deleting_a_record_from_a_recordset).

Para obtener más información acerca de cómo se llevan a cabo las actualizaciones y cómo aparecen las actualizaciones para otros usuarios, vea Conjunto de registros: cómo los conjuntos de [registros actualizan registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Normalmente, al agregar, editar o eliminar un registro, el conjunto de registros cambia el origen de datos inmediatamente. En su lugar, se pueden agrupar las actualizaciones relacionadas en transacciones. Si hay una transacción en progreso, la actualización no es final hasta que se confirma la transacción. Esto permite recuperar o revertir los cambios. Para obtener información acerca de las transacciones, vea [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

La siguiente tabla resume las opciones disponibles para conjuntos de registros con diferentes características de actualización.

### <a name="recordset-readupdate-options"></a>Opciones de lectura y actualización de un conjunto de registros

|Tipo|Lectura|Edición de registro|Eliminación de registro|Adición de nuevos registros (anexar)|
|----------|----------|-----------------|-------------------|------------------------|
|Solo lectura|Y|N|N|N|
|Sólo anexar|Y|N|N|Y|
|Totalmente actualizable|Y|Y|Y|Y|

## <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>Determinar si el conjunto de registros es actualizable

Un objeto de conjunto de registros es actualizable si el origen de datos lo es y se abre el conjunto de registros como actualizable. Su capacidad de actualización depende también de la instrucción SQL utilizada, de la funcionalidad del controlador ODBC y de si la biblioteca de cursores ODBC está o no en memoria. No se puede actualizar un conjunto de registros u origen de datos de sólo lectura.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Para determinar si el conjunto de registros es actualizable

1. Llame a la función miembro [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) del objeto de conjunto de registros.

   `CanUpdate` devuelve un valor distinto de cero si el conjunto de registros es actualizable.

De forma predeterminada, los conjuntos de `AddNew` `Edit`registros `Delete` son totalmente actualizables (puede realizar , , y operaciones). Pero también puede usar la opción [appendOnly](../../mfc/reference/crecordset-class.md#open) para abrir conjuntos de registros actualizables. Un conjunto de registros abierto de esta forma sólo permite agregar nuevos registros con `AddNew`. No se pueden editar ni eliminar registros existentes. Puede probar si un conjunto de registros está abierto solo para anexar mediante una llamada a la [CanAppend](../../mfc/reference/crecordset-class.md#canappend) función miembro. `CanAppend` devuelve un valor distinto de cero si el conjunto de registros es totalmente actualizable o si está abierto solo para anexar.

El código siguiente muestra cómo se puede usar `CanUpdate` para un objeto de conjunto de registros denominado `rsStudentSet`:

```cpp
if( !rsStudentSet.Open( ) )
    return FALSE;
if( !rsStudentSet.CanUpdate( ) )
{
    AfxMessageBox( "Unable to update the Student recordset." );
    return;
}
```

> [!CAUTION]
> Cuando se prepara para actualizar `Update`un conjunto de registros mediante una llamada, tenga cuidado de que el conjunto de registros incluya todas las columnas que componen la clave principal de la tabla (o todas las columnas de cualquier índice único de la tabla). En algunos casos, el marco de trabajo sólo puede utilizar las columnas seleccionadas en el conjunto de registros para identificar qué registro de la tabla se actualiza. Sin todas las columnas necesarias, se podrían actualizar varios registros de la tabla, dañando posiblemente la integridad referencial de ésta. En este caso, el marco de `Update`trabajo produce excepciones cuando se llama a .

## <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>Agregar un registro a un conjunto de registros

Puede agregar nuevos registros a un conjunto de registros si su [CanAppend](../../mfc/reference/crecordset-class.md#canappend) función miembro devuelve un valor distinto de cero.

#### <a name="to-add-a-new-record-to-a-recordset"></a>Para agregar un nuevo registro a un conjunto de registros

1. Asegúrese de que el conjunto de registros es actualizable.

1. Llame a la función miembro [AddNew](../../mfc/reference/crecordset-class.md#addnew) del objeto de conjunto de registros.

   `AddNew` prepara el conjunto de registros para que actúe como búfer de edición. Todos los miembros de datos de campo se establecen en el valor especial Null y se marcan como sin cambios, por lo que solo los valores modificados (sucios) se escriben en el origen de datos cuando se llama a [Update](../../mfc/reference/crecordset-class.md#update).

1. Establezca los valores de los miembros de datos de campo del nuevo registro.

   Asigne valores a los miembros de datos de campo. Aquellos que queden sin asignar no se escriben en el origen de datos.

1. Llame a la `Update` función miembro del objeto de conjunto de registros.

   `Update`completa la adición escribiendo el nuevo registro en el origen de datos. Para obtener información acerca de `Update`las que sucede si no se puede llamar a , vea Conjunto de registros: cómo los conjuntos de [registros actualizan registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Para obtener información sobre cómo funciona la adición de registros y sobre cuándo están visibles los registros agregados en el conjunto de registros, vea Conjunto de [registros: cómo addnew, editar y eliminar trabajo (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).

El siguiente ejemplo muestra cómo agregar un nuevo registro:

```cpp
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
> Para cancelar `AddNew` `Edit` una llamada o una `AddNew` `Edit` llamada, `Move` simplemente realice otra llamada o llame con el *parámetro AFX_MOVE_REFRESH.* Los miembros de datos se restablecen `Add` a sus valores anteriores y usted todavía está en o en `Edit` modo.

## <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>Edición de un registro en un conjunto de registros

Puede editar registros existentes si la función miembro [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) del conjunto de registros devuelve un valor distinto de cero.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Para editar un registro existente en un conjunto de registros

1. Asegúrese de que el conjunto de registros es actualizable.

1. Desplácese al registro que desea actualizar.

1. Llame a la función miembro [Edit](../../mfc/reference/crecordset-class.md#edit) del objeto de conjunto de registros.

   `Edit` prepara el conjunto de registros para que actúe como búfer de edición. Todos los miembros de datos de campo se marcan para que el conjunto de registros pueda detectar posteriormente si se modificaron. Los nuevos valores para los miembros de datos de campo modificados se escriben en el origen de datos cuando se llama a [Update](../../mfc/reference/crecordset-class.md#update).

1. Establezca los valores de los miembros de datos de campo del nuevo registro.

   Asigne valores a los miembros de datos de campo. A los que no asigne valores, permanecen sin modificar.

1. Llame a la `Update` función miembro del objeto de conjunto de registros.

   `Update`completa la edición escribiendo el registro modificado en el origen de datos. Para obtener información acerca de `Update`las que sucede si no se puede llamar a , vea Conjunto de registros: cómo los conjuntos de [registros actualizan registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Después de editar un registro, éste continúa siendo el registro actual.

En el ejemplo `Edit` siguiente se muestra una operación. Se supone que el usuario se desplazó a un registro que desea editar.

```cpp
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
> Para cancelar `AddNew` `Edit` una llamada o una `AddNew` `Edit` llamada, `Move` simplemente realice otra llamada o llame con el *parámetro AFX_MOVE_REFRESH.* Los miembros de datos se restablecen `Add` a sus valores anteriores y usted todavía está en o en `Edit` modo.

## <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>Eliminación de un registro de un conjunto de registros

Puede eliminar registros si la función miembro [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) del conjunto de registros devuelve un valor distinto de cero.

#### <a name="to-delete-a-record"></a>Para eliminar un registro

1. Asegúrese de que el conjunto de registros es actualizable.

1. Desplácese al registro que desea actualizar.

1. Llame a la función miembro [Delete](../../mfc/reference/crecordset-class.md#delete) del objeto de conjunto de registros.

   `Delete`marca inmediatamente el registro como eliminado, tanto en el conjunto de registros como en el origen de datos.

   A `AddNew` `Edit`diferencia `Delete` de `Update` y , no tiene ninguna llamada correspondiente.

1. Desplácese a otro registro.

   > [!NOTE]
   >  Al desplazarse por un conjunto de registros, es posible que no se omitan los registros eliminados. Para obtener más información, vea el [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) función miembro.

En el ejemplo `Delete` siguiente se muestra una operación. Se supone que el usuario se desplazó a un registro que desea eliminar. Después `Delete` se llama, es importante pasar a un nuevo registro.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

Para obtener más información `AddNew`acerca `Edit`de `Delete` los efectos de las funciones , , y miembro, vea Conjunto de registros: cómo los conjuntos de [registros actualizan registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
