---
title: 'Conjunto de registros: Más información acerca de las actualizaciones (ODBC)'
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
ms.openlocfilehash: c29ff110fc507c4e449b2f3d082d98c159a35107
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397775"
---
# <a name="recordset-more-about-updates-odbc"></a>Conjunto de registros: Más información acerca de las actualizaciones (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica:

- [Cómo otras operaciones, como las transacciones, afecta a las actualizaciones](#_core_how_transactions_affect_updates).

- [Las actualizaciones y los de otros usuarios](#_core_your_updates_and_the_updates_of_other_users).

- [Más información acerca de las funciones miembro Update y Delete](#_core_more_about_update_and_delete).

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si ha implementado la obtención masiva de filas, parte de la información no es aplicable. Por ejemplo, no puede llamar a la `AddNew`, `Edit`, `Delete`, y `Update` funciones miembro; sin embargo, puede realizar transacciones. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: Obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_how_other_operations_affect_updates"></a> Cómo otras operaciones afectan a las actualizaciones

Las actualizaciones se ven afectadas por las transacciones en vigor en el momento de la actualización, cerrando el conjunto de registros antes de completar una transacción y desplazando antes de completar una transacción.

###  <a name="_core_how_transactions_affect_updates"></a> Cómo afectan las transacciones a las actualizaciones

Más allá de comprender cómo `AddNew`, `Edit`, y `Delete` trabajo, es importante comprender cómo el `BeginTrans`, `CommitTrans`, y `Rollback` funciones miembro de [CDatabase](../../mfc/reference/cdatabase-class.md) profesional con las funciones de actualización de [CRecordset](../../mfc/reference/crecordset-class.md).

De forma predeterminada, las llamadas a `AddNew` y `Edit` afectan a los datos de origen inmediatamente cuando se llama `Update`. `Delete` llamadas surten efecto inmediatamente. Pero puede establecer una transacción y ejecutar un lote de llamadas de ese tipo. Las actualizaciones no son permanentes hasta que los confirme. Si cambia de opinión, puede revertir la transacción en lugar de confirmarla.

Para obtener más información acerca de las transacciones, vea [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

###  <a name="_core_how_closing_the_recordset_affects_updates"></a> Cómo cerrar el conjunto de registros que afecta a las actualizaciones

Si cierra un conjunto de registros o su asociado `CDatabase` objeto con una transacción en curso (no ha llamado [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) o [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)), se revierte la transacción realice una copia automáticamente (a menos que el back-end de base de datos es el motor de base de datos Microsoft Jet).

> [!CAUTION]
>  Si usa el motor de base de datos Microsoft Jet, cerrar un conjunto de registros dentro de una transacción explícita no da como resultado la liberación de ninguna de las filas modificadas o bloqueos que se colocaron hasta que se confirma o revierte la transacción explícita. Se recomienda abrir y cerrar siempre los conjuntos de registros dentro o fuera de una transacción explícita de Jet.

###  <a name="_core_how_scrolling_affects_updates"></a> Cómo afecta el desplazamiento a las actualizaciones

Cuando se [conjunto de registros: Desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) en un conjunto de registros, el búfer de edición se rellena con cada nuevo registro actual (el registro anterior no se almacena en primer lugar). El desplazamiento pasa a través de los registros eliminados anteriormente. Si se desplaza después un `AddNew` o `Edit` llamada sin llamar a `Update`, `CommitTrans`, o `Rollback` en primer lugar, los cambios se pierden (ninguna advertencia previa) cuando se pone un nuevo registro en el búfer de edición. El búfer de edición se rellena con el registro que se desplaza, se libera el registro almacenado y se produce ningún cambio en el origen de datos. Esto se aplica a ambos `AddNew` y `Edit`.

##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> Las actualizaciones y las actualizaciones de otros usuarios

Cuando se usa un conjunto de registros para actualizar los datos, sus actualizaciones afectan a otros usuarios. De forma similar, las actualizaciones de otros usuarios durante la vigencia del conjunto de registros le afectan.

En un entorno multiusuario, otros usuarios pueden abrir conjuntos de registros que contienen algunos de los mismos registros que ha seleccionado en el conjunto de registros. Los cambios realizados en un registro antes de recuperarlo se reflejan en el conjunto de registros. Debido a conjuntos de registros dinámicos recuperan un registro cada vez que se desplaza a él, reflejan los cambios cada vez que se desplaza a un registro. Las instantáneas de recuperan un registro de la primera vez que se desplaza a él, por lo que las instantáneas sólo reflejan los cambios que se producen antes de que se desplaza al registro inicialmente.

Los registros agregados por otros usuarios después de abrir el conjunto de registros no aparecen en el conjunto de registros, a menos que se volver a consultar. Si el conjunto de registros es de tipo dinámico, las modificaciones realizadas en los registros existentes por otros usuarios se muestran en el conjunto de registros dinámicos cuando se desplaza al registro afectado. Si el conjunto de registros es una instantánea, las modificaciones no se muestran hasta que una nueva consulta de la instantánea. Si desea ver los registros agregados o eliminados por otros usuarios en una instantánea, o los registros agregados por otros usuarios en su conjunto de registros dinámicos, llame a [CRecordset:: Requery](../../mfc/reference/crecordset-class.md#requery) para volver a generar el conjunto de registros. (Tenga en cuenta que las eliminaciones de otros usuarios que aparecen en el conjunto de registros dinámicos.) También se puede llamar a `Requery` para ver los registros agregue, pero no para ver las eliminaciones.

> [!TIP]
>  Para forzar el almacenamiento en caché de toda una instantánea a la vez, llamar a `MoveLast` inmediatamente después de abrir la instantánea. A continuación, llame a `MoveFirst` para empezar a trabajar con los registros. `MoveLast` es equivalente a desplazarse por todos los registros, sino que recupera todas a la vez. Sin embargo, tenga en cuenta que esto puede reducir el rendimiento y podría no ser necesario para algunos controladores.

Los efectos de las actualizaciones en otros usuarios son similares a sus efectos para usted.

##  <a name="_core_more_about_update_and_delete"></a> Más información acerca de Update y Delete

Esta sección proporciona información adicional para ayudarle a trabajar con `Update` y `Delete`.

### <a name="update-success-and-failure"></a>Actualización correctos y erróneos

Si `Update` se realiza correctamente, el `AddNew` o `Edit` finaliza el modo. Para comenzar una `AddNew` o `Edit` modo nuevo, llamada `AddNew` o `Edit`.

Si `Update` se produce un error (devuelve FALSE o inicia una excepción), permanece en `AddNew` o `Edit` modo, dependiendo de qué función llama en último lugar. A continuación, puede realizar uno de los siguientes:

- Modificar un miembro de datos de campo y pruebe el `Update` nuevo.

- Llame a `AddNew` para restablecer los miembros de datos del campo es Null, establezca los valores de los miembros de datos de campo y, a continuación, llamar a `Update` nuevo.

- Llame a `Edit` para volver a cargar los valores que se encontraban en el conjunto de registros antes de la primera llamada a `AddNew` o `Edit`, establezca los valores de los miembros de datos de campo y, a continuación, llame a `Update` nuevo. Después de una correcta `Update` llamar (salvo tras un `AddNew` llamar), los miembros de datos de campo retienen sus nuevos valores.

- Llame a `Move` (incluidos `Move` con un parámetro de AFX_MOVE_REFRESH o 0), que vacía cualquiera cambia y se finaliza cualquier `AddNew` o `Edit` modo vigente.

### <a name="update-and-delete"></a>Update y Delete

En esta sección se aplica a ambos `Update` y `Delete`.

En un `Update` o `Delete` operación, debe actualizarse uno y solo un registro. Dicho registro es el registro actual, que corresponde a los valores de datos en los campos del conjunto de registros. Si por alguna razón, no hay registros se ven afectadas o se ve afectado más de un registro, se produce una excepción que contiene uno de los siguientes **RETCODE** valores:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Cuando se producen estas excepciones, permanece en el `AddNew` o `Edit` que estaba activo cuando llama a `Update` o `Delete`. Estos son los escenarios más comunes en la que vería estas excepciones. Es más probable encontrar en:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED cuando se utiliza el modo de bloqueo optimista y otro usuario modificó el registro de forma que impide que el marco de trabajo que identifica el registro correcto para actualizar o eliminar.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED cuando la tabla que está actualizando no tiene ninguna clave principal o índice único y no tiene suficientes columnas del conjunto de registros para identificar de forma única una fila de tabla.

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: cómo los conjuntos de registros seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Excepciones: excepciones de la base de datos](../../mfc/exceptions-database-exceptions.md)