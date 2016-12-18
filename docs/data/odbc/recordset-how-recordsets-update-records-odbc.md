---
title: "Conjunto de registros: Actualizar los registros (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conjuntos de registros ODBC, actualizar"
  - "registros, actualizar"
  - "conjuntos de registros, editar registros"
  - "conjuntos de registros, actualizar"
  - "actualizar conjuntos de registros"
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conjunto de registros: Actualizar los registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Además de su capacidad de seleccionar registros de un origen de datos, los conjuntos de registros pueden \(opcionalmente\) actualizar o eliminar los registros seleccionados o agregar nuevos registros.  Tres factores determinan la capacidad de actualización de un conjunto de registros: que el origen de datos conectados sea actualizable, las opciones especificadas al crear un objeto de conjunto de registros y el código SQL que se genera.  
  
> [!NOTE]
>  El código SQL en el que se basa el objeto `CRecordset` puede afectar a la capacidad de actualización del conjunto de registros.  Por ejemplo, si el código SQL contiene una combinación o una cláusula **GROUP BY**, MFC establece su propiedad de actualización en **FALSE**.  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si utiliza la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 En este tema se explica:  
  
-   [El rol del programador al actualizar el conjunto de registros](#_core_your_role_in_recordset_updating) y lo que hace el marco de trabajo en favor del usuario.  
  
-   [El conjunto de registros como búfer de edición](#_core_the_edit_buffer) y las [diferencias entre conjuntos de registros dinámicos e instantáneas](#_core_dynasets_and_snapshots).  
  
 [Conjunto de registros: Funcionamiento de AddNew, Edit y Delete \(ODBC\)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) describe las acciones de estas funciones desde el punto de vista del conjunto de registros.  
  
 [Conjunto de registros: Información adicional sobre las actualizaciones \(ODBC\)](../../data/odbc/recordset-more-about-updates-odbc.md) completa los temas de actualización de conjuntos de registros explicando cómo afectan las transacciones a las actualizaciones, cómo afecta el cierre o el desplazamiento en un conjunto de registros a las actualizaciones en progreso, y cómo interactúan sus propias operaciones de actualización con las actualizaciones de otros usuarios.  
  
##  <a name="_core_your_role_in_recordset_updating"></a> El rol del programador al actualizar el conjunto de registros  
 La siguiente tabla muestra el rol del programador al usar conjuntos de registros para agregar, editar o eliminar registros, junto con lo que el marco de trabajo realiza para el programador.  
  
### Actualización del conjunto de registros: el programador y el marco de trabajo  
  
|El programador|El marco de trabajo|  
|--------------------|-------------------------|  
|Determina si el origen de datos es actualizable \(o anexable\).|Proporciona funciones miembro [CDatabase](../../mfc/reference/cdatabase-class.md) para probar la capacidad de actualización o anexación del origen de datos.|  
|Abre un conjunto de registros actualizable \(de cualquier tipo\)||  
|Determina si el conjunto de registros es actualizable llamando a funciones de actualización de `CRecordset` como `CanUpdate` o `CanAppend`.||  
|Llama a las funciones miembro del conjunto de registros para agregar, editar o eliminar registros.|Administra el mecanismo de intercambio de datos entre el objeto de conjunto de registros y el origen de datos.|  
|De forma opcional, utiliza transacciones para controlar el proceso de actualización.|Proporciona funciones miembro de `CDatabase` para admitir las transacciones.|  
  
 Para obtener más información sobre transacciones, vea [Transacción \(ODBC\)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_the_edit_buffer"></a> El búfer de edición  
 Tomados colectivamente, los miembros de datos de campo de un conjunto de registros actúan como búfer de edición que contiene un registro, el registro actual.  Las operaciones de actualización usan este búfer para trabajar sobre el registro actual.  
  
-   Al agregar un registro, se utiliza el búfer de edición para compilar un nuevo registro.  Al terminar de agregar el registro, el registro que anteriormente se consideraba como actual vuelve a ser el registro actual.  
  
-   Al actualizar \(editar\) un registro, el búfer de edición se utiliza para establecer los miembros de datos de campo del conjunto de registros en nuevos valores.  Al terminar la actualización, el registro actualizado sigue siendo el actual.  
  
 Al llamar a [AddNew](../Topic/CRecordset::AddNew.md) o a [Edit](../Topic/CRecordset::Edit.md), se almacena el registro actual para que pueda restaurarse más tarde según sea necesario.  Al llamar a [Delete](../Topic/CRecordset::Delete.md) no se almacena el registro actual, pero se marca como eliminado, y el usuario debe desplazarse a otro registro.  
  
> [!NOTE]
>  El búfer de edición no juega ningún rol en la eliminación de registros.  Al eliminar el registro actual, se marca como eliminado y se considera que el conjunto de registros "no está en ningún registro" hasta que se desplace a un registro diferente.  
  
##  <a name="_core_dynasets_and_snapshots"></a> Conjuntos de registros dinámicos e instantáneas  
 [Las instantáneas](../../data/odbc/dynaset.md) actualizan el contenido de un registro al desplazarse a él.  [Los conjuntos de registros dinámicos](../../data/odbc/snapshot.md) son representaciones estáticas de los registros, por lo que el contenido de un registro no se actualiza hasta que se llama a [Requery](../Topic/CRecordset::Requery.md).  Para poder aprovechar toda la funcionalidad de los conjuntos de registros dinámicos, debe trabajar con un controlador ODBC compatible en el nivel adecuado con la API ODBC.  Para obtener más información, vea [ODBC](../../data/odbc/odbc-basics.md) y [Conjuntos de registros dinámicos](../../data/odbc/dynaset.md).  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Funcionamiento de AddNew, Edit y Delete \(ODBC\)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)