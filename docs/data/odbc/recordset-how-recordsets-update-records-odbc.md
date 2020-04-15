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
ms.openlocfilehash: 03fb696c1fadd834962d37c8e75b5f8910af819e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366978"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Conjunto de registros: Actualizar los registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Además de su capacidad para seleccionar registros de un origen de datos, los conjuntos de registros pueden (opcionalmente) actualizar o eliminar los registros seleccionados o agregar nuevos registros. Tres factores determinan la capacidad de actualización de un conjunto de registros: si el origen de datos conectado es actualizable, las opciones que se especifican al crear un objeto de conjunto de registros y el SQL que se crea.

> [!NOTE]
> El SQL en `CRecordset` el que se basa el objeto puede afectar a la capacidad de actualización del conjunto de registros. Por ejemplo, si el SQL contiene una combinación o una cláusula **GROUP BY,** MFC establece la capacidad de actualización en FALSE.

> [!NOTE]
> Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usa la obtención masiva de filas, vea [Conjunto de registros: obtención de registros en masa (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

En este tema se explica:

- [Su rol en](#_core_your_role_in_recordset_updating) la actualización de conjuntos de registros y lo que el marco de trabajo hace por usted.

- El conjunto de [registros como búfer](#_core_the_edit_buffer) de edición y las [diferencias entre conjuntos de registros dinámicos e instantáneas.](#_core_dynasets_and_snapshots)

Conjunto de [registros: cómo AddNew, Edit y Delete Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) describe las acciones de estas funciones desde el punto de vista del conjunto de registros.

Conjunto de [registros: más información sobre las actualizaciones (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) completa la historia de actualización del conjunto de registros explicando cómo afectan las transacciones a las actualizaciones, cómo el cierre de un conjunto de registros o el desplazamiento afectan a las actualizaciones en curso y cómo interactúan las actualizaciones con las actualizaciones de otros usuarios.

## <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>Su rol en la actualización de conjuntos de registros

En la tabla siguiente se muestra el rol en el uso de conjuntos de registros para agregar, editar o eliminar registros, junto con lo que el marco de trabajo hace por usted.

### <a name="recordset-updating-you-and-the-framework"></a>Actualización de conjuntos de registros: usted y el marco de trabajo

|Los|El marco de trabajo|
|---------|-------------------|
|Determine si el origen de datos es actualizable (o anexable).|Proporciona [CDatabase](../../mfc/reference/cdatabase-class.md) funciones miembro para probar la capacidad de actualización o apendeabilidad del origen de datos.|
|Abra un conjunto de registros actualizable (de cualquier tipo).||
|Determine si el conjunto de `CRecordset` registros es `CanUpdate` `CanAppend`actualizable llamando a funciones de actualización como o .||
|Llame a las funciones miembro del conjunto de registros para agregar, editar y eliminar registros.|Administra la mecánica de intercambio de datos entre el objeto de conjunto de registros y el origen de datos.|
|Opcionalmente, use transacciones para controlar el proceso de actualización.|Proporciona `CDatabase` funciones miembro para admitir transacciones.|

Para obtener más información acerca de las transacciones, vea [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>El búfer de edición

Tomados colectivamente, los miembros de datos de campo de un conjunto de registros sirven como un búfer de edición que contiene un registro: el registro actual. Las operaciones de actualización utilizan este búfer para operar en el registro actual.

- Al agregar un registro, el búfer de edición se utiliza para crear un nuevo registro. Cuando termine de agregar el registro, el registro que anteriormente era actual vuelve a ser actual.

- Al actualizar (editar) un registro, el búfer de edición se utiliza para establecer los miembros de datos de campo del conjunto de registros en nuevos valores. Cuando termine de actualizar, el registro actualizado sigue siendo actual.

Cuando se llama a [AddNew](../../mfc/reference/crecordset-class.md#addnew) o [Edit](../../mfc/reference/crecordset-class.md#edit), el registro actual se almacena para que se pueda restaurar más adelante según sea necesario. Cuando se llama a [Delete](../../mfc/reference/crecordset-class.md#delete), el registro actual no se almacena, pero se marca como eliminado y debe desplazarse a otro registro.

> [!NOTE]
> El búfer de edición no desempeña ningún papel en la eliminación de registros. Al eliminar el registro actual, el registro se marca como eliminado y el conjunto de registros "no está en un registro" hasta que se desplaza a un registro diferente.

## <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>Dynasets e instantáneas

[Los conjuntos de registros dinámicos](../../data/odbc/dynaset.md) actualizan el contenido de un registro a medida que se desplaza hasta el registro. [Las instantáneas](../../data/odbc/snapshot.md) son representaciones estáticas de los registros, por lo que el contenido de un registro no se actualiza a menos que se llame a [Requery](../../mfc/reference/crecordset-class.md#requery). Para usar toda la funcionalidad de los conjuntos de registros dinámicos, debe trabajar con un controlador ODBC que se ajuste al nivel correcto de compatibilidad con la API ODBC. Para obtener más información, vea [ODBC](../../data/odbc/odbc-basics.md) y [Dynaset](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Funcionamiento de AddNew, Edit y Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
