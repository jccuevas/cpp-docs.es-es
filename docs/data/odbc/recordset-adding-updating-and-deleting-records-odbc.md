---
title: "Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddNew (método)"
  - "datos en conjuntos de registros [C++]"
  - "conjuntos de registros ODBC [C++], agregar registros"
  - "conjuntos de registros ODBC [C++], eliminar registros"
  - "conjuntos de registros ODBC [C++], editar registros"
  - "edición de registros [C++]"
  - "edición de registros [C++], en conjuntos de registros"
  - "registros [C++], agregar"
  - "registros [C++], eliminar"
  - "registros [C++], editar"
  - "registros [C++], actualizar"
  - "conjuntos de registros [C++], agregar registros"
  - "conjuntos de registros [C++], eliminar registros"
  - "conjuntos de registros [C++], editar registros"
  - "conjuntos de registros [C++], actualizar"
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
> [!NOTE]
>  Ahora se pueden agregar registros de forma masiva con mayor eficiencia.  Para obtener más información, vea [Conjunto de registros: Agregar registros de forma masiva \(ODBC\)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si utiliza la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Los conjuntos de registros dinámicos y as instantáneas actualizables permiten agregar, editar \(actualizar\) y eliminar registros.  En este tema se explica:  
  
-   [Cómo determinar si un conjunto de registros es actualizable](#_core_determining_whether_your_recordset_is_updatable).  
  
-   [Cómo agregar un nuevo registro](#_core_adding_a_record_to_a_recordset).  
  
-   [Cómo editar un registro existente](#_core_editing_a_record_in_a_recordset).  
  
-   [Cómo eliminar un registro](#_core_deleting_a_record_from_a_recordset).  
  
 Para obtener más información sobre cómo se realizan las actualizaciones y cómo aparecen para el resto de los usuarios, vea [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  Normalmente, al agregar, editar o eliminar un registro, el conjunto de registros cambia el origen de datos inmediatamente.  En su lugar, se pueden agrupar las actualizaciones relacionadas en transacciones.  Si hay una transacción en progreso, la actualización no es final hasta que se confirma la transacción.  Esto permite recuperar o revertir los cambios.  Para obtener información sobre transacciones, vea [Transacción \(ODBC\)](../../data/odbc/transaction-odbc.md).  
  
 La siguiente tabla resume las opciones disponibles para conjuntos de registros con diferentes características de actualización.  
  
### Opciones de lectura y actualización de un conjunto de registros  
  
|Tipo|Leer|Edición de registro|Eliminación de registro|Adición de nuevos registros \(anexar\)|  
|----------|----------|-------------------------|-----------------------------|--------------------------------------------|  
|De sólo lectura|Y|N|N|N|  
|Sólo anexar|Y|N|N|Y|  
|Totalmente actualizable|Y|Y|Y|Y|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> Determinar si un conjunto de registros es actualizable  
 Un objeto de conjunto de registros es actualizable si el origen de datos lo es y se abre el conjunto de registros como actualizable.  Su capacidad de actualización depende también de la instrucción SQL utilizada, de la funcionalidad del controlador ODBC y de si la biblioteca de cursores ODBC está o no en memoria.  No se puede actualizar un conjunto de registros u origen de datos de sólo lectura.  
  
#### Para determinar si el conjunto de registros es actualizable  
  
1.  Llame a la función miembro [CanUpdate](../Topic/CRecordset::CanUpdate.md) del objeto de conjunto de registros.  
  
     `CanUpdate` devuelve un valor distinto de cero si el conjunto de registros es actualizable.  
  
 De forma predeterminada, los conjuntos de registros son totalmente actualizables \(se pueden realizar operaciones `AddNew`, **Edit** y **Delete**\).  También se puede usar la opción [appendOnly](../Topic/CRecordset::Open.md) para abrir conjuntos de registros actualizables.  Un conjunto de registros abierto de esta forma sólo permite agregar nuevos registros con `AddNew`.  No se pueden editar ni eliminar registros existentes.  Puede probar si un conjunto de registros está abierto solo para anexar llamando a la función miembro [CanAppend](../Topic/CRecordset::CanAppend.md).  `CanAppend` devuelve un valor distinto de cero si el conjunto de registros es totalmente actualizable o si está abierto solo para anexar.  
  
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
>  Al prepararse para actualizar un conjunto de registros llamando a **Update**, asegúrese de que incluye todas las columnas que componen la clave principal de la tabla \(o todas las columnas que componen cualquiera de los índices únicos de la tabla\).  En algunos casos, el marco de trabajo sólo puede utilizar las columnas seleccionadas en el conjunto de registros para identificar qué registro de la tabla se actualiza.  Sin todas las columnas necesarias, se podrían actualizar varios registros de la tabla, dañando posiblemente la integridad referencial de ésta.  En este caso, el marco de trabajo produce excepciones al llamar a **Update**.  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a> Agregar un registro a un conjunto de registros  
 Se pueden agregar nuevos registros a un conjunto de registros si su función miembro [CanAppend](../Topic/CRecordset::CanAppend.md) devuelve un valor distinto de cero.  
  
#### Para agregar un nuevo registro a un conjunto de registros  
  
1.  Asegúrese de que el conjunto de registros es actualizable.  
  
2.  Llame a la función miembro [AddNew](../Topic/CRecordset::AddNew.md) del objeto de conjunto de registros.  
  
     `AddNew` prepara el conjunto de registros para que actúe como búfer de edición.  Todos los miembros de datos de campo se establecen en el valor especial Null y se marcan como sin cambios para que sólo se escriban los valores modificados en el origen de datos al llamar a [Update](../Topic/CRecordset::Update.md).  
  
3.  Establezca los valores de los miembros de datos de campo del nuevo registro.  
  
     Asigne valores a los miembros de datos de campo.  Aquellos que queden sin asignar no se escriben en el origen de datos.  
  
4.  Llame a la función miembro **Update** del objeto de conjunto de registros.  
  
     **Update** completa la acción de agregar escribiendo el nuevo registro en el origen de datos.  Para obtener información sobre lo que ocurre si no se llama a **Update**, vea [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Para obtener más información sobre cómo se agregan registros y cuándo son visibles los registros agregados en el conjunto de registros, vea [Conjunto de registros: cómo funcionan AddNew, Edit y Delete \(ODBC\)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).  
  
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
>  Para cancelar una llamada a `AddNew` o **Edit**, basta con realizar otra llamada a `AddNew` o **Edit**; o bien, llamar a **Move** con el parámetro **AFX\_MOVE\_REFRESH**.  Se restaura el valor original de los miembros de datos y el usuario continúa en modo **Edit** o **Add**.  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a> Editar un registro en un conjunto de registros  
 Se pueden editar los registros existentes si la función miembro [CanUpdate](../Topic/CRecordset::CanUpdate.md) del conjunto de registros devuelve un valor distinto de cero.  
  
#### Para editar un registro existente en un conjunto de registros  
  
1.  Asegúrese de que el conjunto de registros es actualizable.  
  
2.  Desplácese al registro que desea actualizar.  
  
3.  Llame a la función miembro [Edit](../Topic/CRecordset::Edit.md) del objeto de conjunto de registros.  
  
     **Edit** prepara el conjunto de registros para que actúe como búfer de edición.  Todos los miembros de datos de campo se marcan para que el conjunto de registros pueda detectar posteriormente si se modificaron.  Los nuevos valores de los miembros de datos de campo modificados se escriben en el origen de datos al llamar a [Update](../Topic/CRecordset::Update.md).  
  
4.  Establezca los valores de los miembros de datos de campo del nuevo registro.  
  
     Asigne valores a los miembros de datos de campo.  A los que no asigne valores, permanecen sin modificar.  
  
5.  Llame a la función miembro **Update** del objeto de conjunto de registros.  
  
     **Update** completa la acción de editar escribiendo el registro modificado en el origen de datos.  Para obtener información sobre lo que ocurre si no se llama a **Update**, vea [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Después de editar un registro, éste continúa siendo el registro actual.  
  
 El siguiente ejemplo muestra una operación **Edit**.  Se supone que el usuario se desplazó a un registro que desea editar.  
  
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
>  Para cancelar una llamada a `AddNew` o **Edit**, basta con realizar otra llamada a `AddNew` o **Edit**; o bien, llamar a **Move** con el parámetro **AFX\_MOVE\_REFRESH**.  Se restaura el valor original de los miembros de datos y el usuario continúa en modo **Edit** o **Add**.  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a> Eliminar un registro de un conjunto de registros  
 Se pueden eliminar los registros existentes si la función miembro [CanUpdate](../Topic/CRecordset::CanUpdate.md) del conjunto de registros devuelve un valor distinto de cero.  
  
#### Para eliminar un registro  
  
1.  Asegúrese de que el conjunto de registros es actualizable.  
  
2.  Desplácese al registro que desea actualizar.  
  
3.  Llame a la función miembro [Delete](../Topic/CRecordset::Delete.md) del objeto de conjunto de registros.  
  
     **Delete** marca inmediatamente el registro como eliminado, tanto en el conjunto de registros como en el origen de datos.  
  
     A diferencia de `AddNew` y **Edit**, **Delete** no tiene una llamada a **Update** correspondiente.  
  
4.  Desplácese a otro registro.  
  
    > [!NOTE]
    >  Al desplazarse por un conjunto de registros, es posible que no se omitan los registros eliminados.  Para obtener más información, vea la función miembro [IsDeleted](../Topic/CRecordset::IsDeleted.md).  
  
 El siguiente ejemplo muestra una operación **Delete**.  Se supone que el usuario se desplazó a un registro que desea eliminar.  Después de llamar a **Delete**, se debe desplazar a un nuevo registro.  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
 Para obtener más información sobre los efectos de las funciones miembro `AddNew`, **Edit** y **Delete**, vea [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Bloquear registros \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)