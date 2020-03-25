---
title: 'Conjunto de registros: Actualizar los registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: 578b3b39d90b3beb80dbd201d4982fee30dc6bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212880"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Conjunto de registros: Actualizar los registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Además de su capacidad para seleccionar registros de un origen de datos, los conjuntos de registros pueden (opcionalmente) actualizar o eliminar los registros seleccionados o agregar nuevos registros. Tres factores determinan la actualización de un conjunto de registros: Si el origen de datos conectado es actualizable, las opciones que se especifican al crear un objeto de conjunto de registros y el SQL que se crea.

> [!NOTE]
>  El SQL en el que se basa el objeto de `CRecordset` puede afectar a la actualización de la actualización del conjunto de registros. Por ejemplo, si el SQL contiene una combinación o una cláusula **Group by** , MFC establece la función de actualización en false.

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usa la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

En este tema se explica:

- [Su rol en la actualización de conjuntos de registros](#_core_your_role_in_recordset_updating) y lo que hace el marco de trabajo.

- [El conjunto de registros como un búfer de edición](#_core_the_edit_buffer) y las [diferencias entre dynasets e instantáneas](#_core_dynasets_and_snapshots).

[Conjunto de registros: Cómo funciona AddNew, Edit y Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) describe las acciones de estas funciones desde el punto de vista del conjunto de registros.

[Conjunto de registros: más información sobre las actualizaciones (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) completa la historia de actualización del conjunto de registros explicando cómo afectan las transacciones a las actualizaciones, cómo el cierre de un conjunto de registros o el desplazamiento afecta a las actualizaciones en curso, y cómo interactúan las actualizaciones con las actualizaciones de otros usuarios.

##  <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>Su rol en la actualización de conjuntos de registros

En la tabla siguiente se muestra el rol del uso de conjuntos de registros para agregar, editar o eliminar registros, junto con lo que hace el marco de trabajo.

### <a name="recordset-updating-you-and-the-framework"></a>Actualización de conjuntos de registros: usted y el marco

|Los|El marco de trabajo|
|---------|-------------------|
|Determinar si el origen de datos es actualizable (o anexable).|Proporciona funciones miembro de [CDatabase](../../mfc/reference/cdatabase-class.md) para probar la actualización o la anexabilidad del origen de datos.|
|Abra un conjunto de registros actualizable (de cualquier tipo).||
|Determine si el conjunto de registros se actualiza mediante una llamada a `CRecordset` funciones de actualización como `CanUpdate` o `CanAppend`.||
|Llame a las funciones miembro de conjunto de registros para agregar, editar y eliminar registros.|Administra la mecánica de intercambiar datos entre el objeto de conjunto de registros y el origen de datos.|
|Opcionalmente, puede utilizar transacciones para controlar el proceso de actualización.|Proporciona funciones miembro de `CDatabase` para admitir transacciones.|

Para obtener más información acerca de las transacciones, vea [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>Búfer de edición

En conjunto, los miembros de datos de campo de un conjunto de registros sirven como búfer de edición que contiene un registro: el registro actual. Las operaciones de actualización utilizan este búfer para operar en el registro actual.

- Al agregar un registro, el búfer de edición se usa para crear un nuevo registro. Cuando termine de agregar el registro, el registro que se actualizó previamente vuelve a ser actual.

- Al actualizar (editar) un registro, el búfer de edición se usa para establecer los miembros de datos de campo del conjunto de registros en nuevos valores. Al finalizar la actualización, el registro actualizado sigue siendo actual.

Cuando se llama a [AddNew](../../mfc/reference/crecordset-class.md#addnew) o [Edit](../../mfc/reference/crecordset-class.md#edit), el registro actual se almacena para que se pueda restaurar más adelante según sea necesario. Cuando se llama a [Delete](../../mfc/reference/crecordset-class.md#delete), el registro actual no se almacena, sino que se marca como eliminado y debe desplazarse a otro registro.

> [!NOTE]
>  El búfer de edición no juega ningún rol en la eliminación de registros. Al eliminar el registro actual, el registro se marca como eliminado y el conjunto de registros es "no en un registro" hasta que se desplaza a otro registro.

##  <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>Dynasets e instantáneas

Los [conjuntos de registros dinámicos](../../data/odbc/dynaset.md) actualizan el contenido de un registro a medida que se desplaza al registro. Las [instantáneas](../../data/odbc/snapshot.md) son representaciones estáticas de los registros, por lo que no se actualiza el contenido de un registro a menos que llame a [Requery](../../mfc/reference/crecordset-class.md#requery). Para usar toda la funcionalidad de los conjuntos de registros dinámicos, debe trabajar con un controlador ODBC que se ajuste al nivel correcto de compatibilidad con la API de ODBC. Para obtener más información, vea [ODBC](../../data/odbc/odbc-basics.md) y [Dynaset](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Funcionamiento de AddNew, Edit y Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
