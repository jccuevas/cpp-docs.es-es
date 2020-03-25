---
title: 'Conjunto de registros: Información adicional sobre las actualizaciones (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
ms.openlocfilehash: f11c723e4589cb28a3f38100050a69a78fc0809e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212854"
---
# <a name="recordset-more-about-updates-odbc"></a>Conjunto de registros: Información adicional sobre las actualizaciones (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica:

- [El modo en que otras operaciones, como las transacciones, afectan a las actualizaciones](#_core_how_transactions_affect_updates).

- [Sus actualizaciones y las de otros usuarios](#_core_your_updates_and_the_updates_of_other_users).

- [Más información sobre las funciones miembro Update y DELETE](#_core_more_about_update_and_delete).

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si ha implementado la obtención masiva de filas, parte de la información no se aplica. Por ejemplo, no puede llamar a las funciones miembro `AddNew`, `Edit`, `Delete`y `Update`. sin embargo, puede realizar transacciones. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>Cómo afectan las otras operaciones a las actualizaciones

Las actualizaciones se ven afectadas por las transacciones en vigor en el momento de la actualización, cerrando el conjunto de registros antes de completar una transacción y desplazándose antes de completar una transacción.

###  <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>Cómo afectan las transacciones a las actualizaciones

Además de comprender cómo `AddNew`, `Edit`y `Delete` funcionan, es importante comprender cómo funcionan las funciones miembro `BeginTrans`, `CommitTrans`y `Rollback` de [CDatabase](../../mfc/reference/cdatabase-class.md) con las funciones de actualización de [CRecordset](../../mfc/reference/crecordset-class.md).

De forma predeterminada, las llamadas a `AddNew` y `Edit` afectan al origen de datos inmediatamente cuando se llama a `Update`. las llamadas `Delete` surten efecto inmediatamente. Sin embargo, puede establecer una transacción y ejecutar un lote de esas llamadas. Las actualizaciones no son permanentes hasta que se confirman. Si cambia de opinión, puede revertir la transacción en lugar de confirmarla.

Para obtener más información acerca de las transacciones, vea [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

###  <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>Cómo el cierre del conjunto de registros afecta a las actualizaciones

Si cierra un conjunto de registros o su objeto `CDatabase` asociado con una transacción en curso (no ha llamado a [CDatabase:: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) o [CDatabase:: Rollback](../../mfc/reference/cdatabase-class.md#rollback)), la transacción se revierte automáticamente (a menos que el back-end de la base de datos sea el motor de base de datos de Microsoft Jet).

> [!CAUTION]
>  Si usa el motor de base de datos de Microsoft Jet, el cierre de un conjunto de registros dentro de una transacción explícita no producirá la liberación de las filas modificadas o bloqueos que se hayan colocado hasta que se confirme o se revierta la transacción explícita. Se recomienda que siempre se abran y cierren conjuntos de registros dentro o fuera de una transacción jet explícita.

###  <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>Cómo afecta el desplazamiento a las actualizaciones

Cuando se registra [: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) en un conjunto de registros, el búfer de edición se rellena con cada nuevo registro actual (el registro anterior no se almacena primero). El desplazamiento omite los registros eliminados previamente. Si se desplaza después de una llamada `AddNew` o `Edit` sin llamar primero a `Update`, `CommitTrans`o `Rollback`, se perderán todos los cambios (sin ninguna advertencia) cuando se introduzca un nuevo registro en el búfer de edición. El búfer de edición se rellena con el registro desplazado, el registro almacenado se libera y no se produce ningún cambio en el origen de datos. Esto se aplica a `AddNew` y `Edit`.

##  <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>Actualizaciones y actualizaciones de otros usuarios

Cuando se utiliza un conjunto de registros para actualizar datos, las actualizaciones afectan a otros usuarios. Del mismo modo, las actualizaciones de otros usuarios durante la vigencia del conjunto de registros le afectan.

En un entorno multiusuario, otros usuarios pueden abrir conjuntos de registros que contengan algunos de los mismos registros que ha seleccionado en el conjunto de registros. Los cambios en un registro antes de recuperarlo se reflejan en el conjunto de registros. Dado que los dynasets recuperan un registro cada vez que se desplaza a él, los conjuntos de registros dinámicos reflejan los cambios cada vez que se desplaza a un registro. Las instantáneas recuperan un registro la primera vez que se desplaza a él, por lo que las instantáneas reflejan solo los cambios que se producen antes de desplazarse al registro inicialmente.

Los registros agregados por otros usuarios después de abrir el conjunto de registros no aparecen en el conjunto de registros a menos que vuelva a realizar la consulta. Si el conjunto de registros es un Dynaset, los cambios en los registros existentes por otros usuarios se muestran en el conjunto de registros dinámico al desplazarse al registro afectado. Si el conjunto de registros es una instantánea, las modificaciones no se muestran hasta que se reconsulta la instantánea. Si desea ver registros agregados o eliminados por otros usuarios en la instantánea, o registros agregados por otros usuarios en el conjunto de registros dinámicos, llame a [CRecordset:: Requery](../../mfc/reference/crecordset-class.md#requery) para volver a generar el conjunto de registros. (Tenga en cuenta que las eliminaciones de otros usuarios se muestran en el conjunto de registros dinámico). También puede llamar a `Requery` para ver los registros que agregue, pero no para ver las eliminaciones.

> [!TIP]
>  Para forzar el almacenamiento en caché de una instantánea completa al mismo tiempo, llame a `MoveLast` inmediatamente después de abrir la instantánea. A continuación, llame a `MoveFirst` para empezar a trabajar con los registros. `MoveLast` es equivalente a desplazarse por todos los registros, pero los recupera todos a la vez. Sin embargo, tenga en cuenta que esto puede reducir el rendimiento y puede que no sea necesario para algunos controladores.

Los efectos de las actualizaciones en otros usuarios son similares a sus efectos.

##  <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>Más información acerca de Update y DELETE

En esta sección se proporciona información adicional para ayudarle a trabajar con `Update` y `Delete`.

### <a name="update-success-and-failure"></a>Actualización correcta y errónea

Si `Update` se realiza correctamente, finaliza el modo de `AddNew` o `Edit`. Para volver a iniciar un `AddNew` o `Edit` modo, llame a `AddNew` o `Edit`.

Si `Update` produce un error (devuelve FALSE o produce una excepción), permanece en el modo de `AddNew` o `Edit`, en función de la función a la que llamó en último lugar. y podrá realizar una de las siguientes acciones:

- Modifique un miembro de datos de campo y vuelva a intentar el `Update`.

- Llame a `AddNew` para restablecer los miembros de datos de campo en null, establezca los valores de los miembros de datos de campo y, a continuación, vuelva a llamar a `Update`.

- Llame a `Edit` para volver a cargar los valores que estaban en el conjunto de registros antes de la primera llamada a `AddNew` o `Edit`, establezca los valores de los miembros de datos de campo y, a continuación, vuelva a llamar a `Update`. Después de una llamada `Update` correcta (excepto después de una llamada `AddNew`), los miembros de datos de campo conservan sus nuevos valores.

- Llame a `Move` (incluido `Move` con un parámetro de AFX_MOVE_REFRESH o 0), que vacía los cambios y finaliza cualquier `AddNew` o `Edit` modo en vigor.

### <a name="update-and-delete"></a>Actualizar y eliminar

Esta sección se aplica tanto a `Update` como a `Delete`.

En una operación `Update` o `Delete`, solo se debe actualizar un registro. Ese registro es el registro actual, que corresponde a los valores de datos de los campos del conjunto de registros. Si, por alguna razón, no se ven afectados los registros o se ve afectado más de un registro, se produce una excepción que contiene uno de los siguientes valores de **RETCODE** :

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Cuando se produzcan estas excepciones, permanecerá en el `AddNew` o `Edit` estado en el que se encontraba cuando llamó a `Update` o `Delete`. Estos son los escenarios más comunes en los que se verán estas excepciones. Lo más probable es que vea lo siguiente:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED cuando se usa el modo de bloqueo optimista y otro usuario ha modificado el registro de forma que impide que el marco de trabajo identifique el registro correcto que se va a actualizar o eliminar.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED cuando la tabla que está actualizando no tiene una clave principal o un índice único y no tiene suficientes columnas en el conjunto de registros para identificar de forma única una fila de la tabla.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Excepciones: Excepciones de base de datos](../../mfc/exceptions-database-exceptions.md)
