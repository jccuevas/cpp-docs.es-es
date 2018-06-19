---
title: 'Conjunto de registros: Actualizar los registros (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b16faf4c5ef0208c946cff123ecbe62b513e65ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092462"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Conjunto de registros: Actualizar los registros (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Además de su capacidad para seleccionar los registros de un origen de datos, conjuntos de registros pueden (opcionalmente) actualizar o eliminar los registros seleccionados o agregar nuevos registros. Tres factores determinan la capacidad de actualización de un conjunto de registros: si el origen de datos conectado es actualizable, las opciones que especifique cuando se crea un objeto de conjunto de registros y el código SQL que se crea.  
  
> [!NOTE]
>  El código SQL en el que su `CRecordset` se basa el objeto pueden afectar a la capacidad de actualización del conjunto de registros. Por ejemplo, si el código SQL contiene una combinación o un **GROUP BY** cláusula, MFC establece su propiedad de actualización en **FALSE**.  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si se usa la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 En este tema se explica:  
  
-   [El rol de actualizar el conjunto de registros](#_core_your_role_in_recordset_updating) y lo que hace el marco de trabajo para usted.  
  
-   [El conjunto de registros como búfer de edición](#_core_the_edit_buffer) y [diferencias entre los conjuntos de registros dinámicos e instantáneas](#_core_dynasets_and_snapshots).  
  
 [Conjunto de registros: Cómo AddNew, Edit y Delete trabajo (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) describe las acciones de estas funciones desde el punto de vista del conjunto de registros.  
  
 [Conjunto de registros: Más sobre las actualizaciones (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) completa el caso de actualización del conjunto de registros y explica cómo afectan las transacciones a las actualizaciones, cómo cerrar un conjunto de registros o el desplazamiento afecta a las actualizaciones en curso y cómo interactúan las actualizaciones con las actualizaciones de otros usuarios.  
  
##  <a name="_core_your_role_in_recordset_updating"></a> El rol de actualizar el conjunto de registros  
 La siguiente tabla muestra su rol en el uso de conjuntos de registros para agregar, editar o eliminar registros, junto con lo que hace el marco de trabajo para usted.  
  
### <a name="recordset-updating-you-and-the-framework"></a>Actualizar el conjunto de registros: El y el marco de trabajo  
  
|El programador|El marco de trabajo|  
|---------|-------------------|  
|Determina si el origen de datos es actualizable (o anexable).|Fuentes de [CDatabase](../../mfc/reference/cdatabase-class.md) funciones miembro para probar los capacidad de actualización o anexación del origen de datos.|  
|Abra un conjunto de registros actualizable (de cualquier tipo).||  
|Determinar si el conjunto de registros es actualizable mediante una llamada a `CRecordset` actualizar funciones como `CanUpdate` o `CanAppend`.||  
|Llamar a funciones miembro para agregar, editar y eliminar registros de conjunto de registros.|Administra los mecanismos de intercambio de datos entre el objeto de conjunto de registros y el origen de datos.|  
|Si lo desea, puede utilizar transacciones para controlar el proceso de actualización.|Fuentes de `CDatabase` las funciones de miembro para admitir las transacciones.|  
  
 Para obtener más información acerca de las transacciones, vea [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_the_edit_buffer"></a> El búfer de edición  
 Tomados colectivamente, los miembros de datos de campo de un conjunto de registros actúan como búfer de edición que contiene un registro, el registro actual. Las operaciones de actualización usan este búfer para operar en el registro actual.  
  
-   Cuando se agrega un registro, el búfer de edición se utiliza para crear un nuevo registro. Cuando termine de agregar el registro, el registro que era anteriormente actual vuelve actual.  
  
-   Al actualizar (Editar) un registro, la edición búfer se utiliza para establecer a los miembros de datos de campo del conjunto de registros a los nuevos valores. Cuando termine de actualizar, el registro actualizado sigue estando actualizado.  
  
 Cuando se llama a [AddNew](../../mfc/reference/crecordset-class.md#addnew) o [editar](../../mfc/reference/crecordset-class.md#edit), se almacena el registro actual para que pueda restaurarse más tarde según sea necesario. Cuando se llama a [eliminar](../../mfc/reference/crecordset-class.md#delete), no se almacena el registro actual, pero se marca como eliminado y debe desplazar a otro registro.  
  
> [!NOTE]
>  El búfer de edición desempeña ningún papel en la eliminación del registro. Cuando se elimina el registro actual, el registro se marca como eliminado, y el conjunto de registros es "no está en un registro" hasta que se desplaza a un registro diferente.  
  
##  <a name="_core_dynasets_and_snapshots"></a> Conjuntos de registros dinámicos e instantáneas  
 [Conjuntos de registros dinámicos](../../data/odbc/dynaset.md) actualizar el contenido de un registro mientras se desplaza al registro. [Las instantáneas](../../data/odbc/snapshot.md) son representaciones estáticas de los registros, por lo que no se actualiza el contenido de un registro a menos que llame a [Requery](../../mfc/reference/crecordset-class.md#requery). Para usar todas las funciones de conjuntos de registros dinámicos, debe estar trabajando con un controlador ODBC que se ajusta del nivel de compatibilidad con la API de ODBC adecuado. Para obtener más información, consulte [ODBC](../../data/odbc/odbc-basics.md) y [Dynaset](../../data/odbc/dynaset.md).  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Funcionamiento de AddNew, Edit y Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)