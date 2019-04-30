---
title: 'Conjunto de registros: Cómo actualizar los registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: bf71f562714e2dacfe75540e1e532219b3eb307f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397814"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Conjunto de registros: Cómo actualizar los registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Además de su capacidad para seleccionar registros de un origen de datos, conjuntos de registros pueden (opcionalmente) actualizar o eliminar los registros seleccionados o agregar nuevos registros. Tres factores determinan la capacidad de actualización de un conjunto de registros: si el origen de datos conectado es actualizable, las opciones especificadas al crear un objeto de conjunto de registros y el código SQL que se crea.

> [!NOTE]
>  El código SQL en el que su `CRecordset` se basa el objeto pueden afectar a la capacidad de actualización del conjunto de registros. Por ejemplo, si su SQL contiene una combinación o un **GROUP BY** cláusula, MFC establece su propiedad de actualización en FALSE.

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usas la obtención masiva de filas, vea [conjunto de registros: Obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

En este tema se explica:

- [Su rol en la actualización del conjunto de registros](#_core_your_role_in_recordset_updating) y lo que hace el marco de trabajo para usted.

- [El conjunto de registros como un búfer de edición](#_core_the_edit_buffer) y [diferencias entre los conjuntos de registros dinámicos y las instantáneas](#_core_dynasets_and_snapshots).

[Conjunto de registros: Cómo AddNew, Edit y Delete trabajo (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) se describen las acciones de estas funciones desde el punto de vista del conjunto de registros.

[Conjunto de registros: Más sobre las actualizaciones (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) se completa la historia de actualización del conjunto de registros, explique cómo afectan las transacciones a las actualizaciones, cómo cerrar un conjunto de registros o el desplazamiento afecta a las actualizaciones en curso y cómo interactúan las actualizaciones con las actualizaciones de otros usuarios.

##  <a name="_core_your_role_in_recordset_updating"></a> Su rol en la actualización del conjunto de registros

En la tabla siguiente se muestra su rol en usar conjuntos de registros para agregar, editar o eliminar registros, junto con lo que hace el marco de trabajo para usted.

### <a name="recordset-updating-you-and-the-framework"></a>Actualizando el conjunto de registros: Usted y el marco de trabajo

|El programador|El marco de trabajo|
|---------|-------------------|
|Determinar si el origen de datos es actualizable (o anexable).|Suministros [CDatabase](../../mfc/reference/cdatabase-class.md) funciones miembro para probar el origen de datos updateability o anexación.|
|Abra un conjunto de registros actualizable (de cualquier tipo).||
|Determinar si el conjunto de registros es actualizable mediante una llamada a `CRecordset` actualizar funciones como `CanUpdate` o `CanAppend`.||
|Llamar a funciones miembro para agregar, editar y eliminar registros de conjunto de registros.|Administra el mecanismo de intercambio de datos entre el objeto de conjunto de registros y el origen de datos.|
|Si lo desea, puede utilizar transacciones para controlar el proceso de actualización.|Suministros `CDatabase` las funciones de miembro para admitir transacciones.|

Para obtener más información acerca de las transacciones, vea [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="_core_the_edit_buffer"></a> El búfer de edición

Tomados colectivamente, los miembros de un conjunto de registros de datos de campo actúan como un búfer de edición que contiene un registro, el registro actual. Las operaciones de actualización usan este búfer para operar en el registro actual.

- Cuando se agrega un registro, el búfer de edición se usa para generar un nuevo registro. Cuando termine de agregar el registro, el registro actual anterior vuelve a actual.

- Cuando se actualiza un registro, la edición (edit) búfer se usa para establecer a los miembros de datos de campo del conjunto de registros con los nuevos valores. Cuando termine de actualizar, es aún actual del registro actualizado.

Cuando se llama a [AddNew](../../mfc/reference/crecordset-class.md#addnew) o [editar](../../mfc/reference/crecordset-class.md#edit), se almacena el registro actual, por lo que se puede restaurar posteriormente según sea necesario. Cuando se llama a [eliminar](../../mfc/reference/crecordset-class.md#delete), no se almacena el registro actual, pero se marca como eliminada y que debe desplazarse a otro registro.

> [!NOTE]
>  El búfer de edición desempeña ningún papel en la eliminación de registros. Cuando se elimina el registro actual, el registro se marca como eliminado, y el conjunto de registros es "no está en un registro" hasta que se desplaza a un registro diferente.

##  <a name="_core_dynasets_and_snapshots"></a> Conjuntos de registros dinámicos y las instantáneas

[Conjuntos de registros dinámicos](../../data/odbc/dynaset.md) actualizan el contenido de un registro al desplazarse al registro. [Las instantáneas](../../data/odbc/snapshot.md) son representaciones estáticas de los registros, por lo que no se actualiza el contenido de un registro a menos que llame a [Requery](../../mfc/reference/crecordset-class.md#requery). Para usar todas las funciones de conjuntos de registros dinámicos, debe estar trabajando con un controlador ODBC que se ajusta al nivel correcto de la compatibilidad con la API de ODBC. Para obtener más información, consulte [ODBC](../../data/odbc/odbc-basics.md) y [Dynaset](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: funcionamiento de AddNew, Edit y Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)