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
ms.openlocfilehash: 955b26137ce976514d84f95f4d819779b93bd78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368676"
---
# <a name="recordset-more-about-updates-odbc"></a>Conjunto de registros: Información adicional sobre las actualizaciones (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica:

- [Cómo afectan otras operaciones, como las transacciones, a las actualizaciones.](#_core_how_transactions_affect_updates)

- [Sus actualizaciones y las de otros usuarios.](#_core_your_updates_and_the_updates_of_other_users)

- [Más información sobre las funciones miembro Update y Delete](#_core_more_about_update_and_delete).

> [!NOTE]
> Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si ha implementado la obtención masiva de filas, parte de la información no se aplica. Por ejemplo, no `AddNew`puede `Edit` `Delete`llamar `Update` a las funciones miembro , , y ; sin embargo, puede realizar transacciones. Para obtener más información acerca de la obtención masiva de filas, vea [Conjunto de registros: obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>Cómo afectan otras operaciones a las actualizaciones

Las actualizaciones se ven afectadas por las transacciones en vigor en el momento de la actualización, cerrando el conjunto de registros antes de completar una transacción y desplazándose antes de completar una transacción.

### <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>Cómo afectan las transacciones a las actualizaciones

Además `AddNew` `Edit`de `Delete` comprender cómo , , y `BeginTrans` `CommitTrans`trabajar, `Rollback` es importante comprender cómo funcionan las funciones , , y miembro de [CDatabase](../../mfc/reference/cdatabase-class.md) con las funciones de actualización de [CRecordset](../../mfc/reference/crecordset-class.md).

De forma predeterminada, llama `AddNew` al origen de datos y `Edit` afecta inmediatamente al origen de datos cuando se llama a `Update`archivos . `Delete`las llamadas surten efecto inmediatamente. Pero puede establecer una transacción y ejecutar un lote de este tipo de llamadas. Las actualizaciones no son permanentes hasta que las confirme. Si cambia de opinión, puede revertir la transacción en lugar de confirmarla.

Para obtener más información acerca de las transacciones, vea [Transacción (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>Cómo el cierre del conjunto de registros afecta a las actualizaciones

Si cierra un conjunto de `CDatabase` registros, o su objeto asociado, con una transacción en curso (no ha llamado [a CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) o [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)), la transacción se revierte automáticamente (a menos que el back-end de la base de datos sea el motor de base de datos de Microsoft Jet).

> [!CAUTION]
> Si usa el motor de base de datos Microsoft Jet, cerrar un conjunto de registros dentro de una transacción explícita no da como resultado liberar ninguna de las filas que se modificaron o bloqueos que se colocaron hasta que se confirma o revierte la transacción explícita. Se recomienda que siempre abra y cierre conjuntos de registros dentro o fuera de una transacción Jet explícita.

### <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>Cómo afecta el desplazamiento a las actualizaciones

Cuando [Recordset: Desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) en un conjunto de registros, el búfer de edición se rellena con cada nuevo registro actual (el registro anterior no se almacena primero). El desplazamiento omite los registros eliminados anteriormente. Si se desplaza `AddNew` `Edit` después `Update`de `CommitTrans`una `Rollback` llamada o sin llamar a , , o primero, los cambios se pierden (sin advertencia) a medida que se introduce un nuevo registro en el búfer de edición. El búfer de edición se rellena con el registro desplazado, el registro almacenado se libera y no se produce ningún cambio en el origen de datos. Esto se aplica a `AddNew` y `Edit`.

## <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>Sus actualizaciones y las actualizaciones de otros usuarios

Cuando se utiliza un conjunto de registros para actualizar datos, las actualizaciones afectan a otros usuarios. Del mismo modo, las actualizaciones de otros usuarios durante la duración del conjunto de registros le afectan.

En un entorno multiusuario, otros usuarios pueden abrir conjuntos de registros que contienen algunos de los mismos registros que ha seleccionado en el conjunto de registros. Los cambios en un registro antes de recuperarlo se reflejan en el conjunto de registros. Dado que los conjuntos de registros dinámicos recuperan un registro cada vez que se desplaza hasta él, los conjuntos de registros dinámicos reflejan los cambios cada vez que se desplaza a un registro. Las instantáneas recuperan un registro la primera vez que se desplaza a él, por lo que las instantáneas reflejan solo los cambios que se producen antes de desplazarse al registro inicialmente.

Los registros agregados por otros usuarios después de abrir el conjunto de registros no se muestran en el conjunto de registros a menos que vuelva a consultar. Si el conjunto de registros es un conjunto de registros dinámicos, las ediciones de registros existentes por otros usuarios se muestran en el conjunto de registros dinámicos cuando se desplaza al registro afectado. Si el conjunto de registros es una instantánea, las ediciones no se muestran hasta que vuelva a consultar la instantánea. Si desea ver registros agregados o eliminados por otros usuarios en la instantánea, o registros agregados por otros usuarios en el conjunto de registros dinámicos, llame a [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) para volver a generar el conjunto de registros. (Tenga en cuenta que las eliminaciones de otros usuarios aparecen en su conjunto de registros dinámicos.) También puede `Requery` llamar para ver los registros que agrega, pero no para ver las eliminaciones.

> [!TIP]
> Para forzar el almacenamiento en caché `MoveLast` de una instantánea completa a la vez, llame inmediatamente después de abrir la instantánea. Luego `MoveFirst` llame para comenzar a trabajar con los registros. `MoveLast`es equivalente a desplazarse por todos los registros, pero los recupera todos a la vez. Tenga en cuenta, sin embargo, que esto puede reducir el rendimiento y podría no ser necesario para algunos controladores.

Los efectos de sus actualizaciones en otros usuarios son similares a sus efectos en usted.

## <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>Más información sobre Actualizar y eliminar

Esta sección proporciona información adicional `Update` para `Delete`ayudarle a trabajar con y .

### <a name="update-success-and-failure"></a>Actualizar éxito y fracaso

Si `Update` se realiza `AddNew` `Edit` correctamente, el modo o finaliza. Para iniciar `AddNew` `Edit` un modo `AddNew` o `Edit`de nuevo, llame o .

Si `Update` se produce un error (devuelve FALSE `AddNew` `Edit` o produce una excepción), permanece en o modo, dependiendo de la función que llamó último. y podrá realizar una de las siguientes acciones:

- Modifique un miembro de `Update` datos de campo e inténtelo de nuevo.

- Llame `AddNew` para restablecer los miembros de datos de campo a Null, establezca los valores de los miembros de datos de campo y, a continuación, vuelva a llamar. `Update`

- Llame `Edit` para volver a cargar los valores que `AddNew` `Edit`estaban en el conjunto de registros `Update` antes de la primera llamada a o , establezca los valores de los miembros de datos de campo y, a continuación, vuelva a llamar. Después `Update` de una llamada `AddNew` correcta (excepto después de una llamada), los miembros de datos de campo conservan sus nuevos valores.

- Llamada `Move` (incluso `Move` con un parámetro de AFX_MOVE_REFRESH, o 0), `AddNew` `Edit` que vacía cualquier cambio y finaliza cualquier modo o modo en vigor.

### <a name="update-and-delete"></a>Actualizar y eliminar

Esta sección se `Update` `Delete`aplica tanto a .

En `Update` una `Delete` operación, solo se debe actualizar un registro. Ese registro es el registro actual, que corresponde a los valores de datos en los campos del conjunto de registros. Si por alguna razón no se ve afectado ningún registro o se ve afectado más de un registro, se produce una excepción que contiene uno de los siguientes valores **RETCODE:**

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Cuando se producen estas excepciones, `AddNew` permanece `Edit` en el estado `Update` o `Delete`en el que se encontraban cuando llamó o . Estos son los escenarios más comunes en los que vería estas excepciones. Es más probable que veas:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED cuando se utiliza el modo de bloqueo optimista y otro usuario ha modificado el registro de una manera que impide que el marco de trabajo identifique el registro correcto para actualizar o eliminar.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED cuando la tabla que está actualizando no tiene ninguna clave principal o índice único y no tiene suficientes columnas en el conjunto de registros para identificar de forma única una fila de tabla.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Excepciones: Excepciones de base de datos](../../mfc/exceptions-database-exceptions.md)
