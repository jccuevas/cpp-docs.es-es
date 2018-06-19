---
title: 'Conjunto de registros: Más información acerca de las actualizaciones (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ea46e0462f3763e04ec18ad9bff2b0d3ded1deee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098672"
---
# <a name="recordset-more-about-updates-odbc"></a>Conjunto de registros: Información adicional sobre las actualizaciones (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 En este tema se explica:  
  
-   [Cómo afectan otras operaciones, como las transacciones, a las actualizaciones](#_core_how_transactions_affect_updates).  
  
-   [Las actualizaciones y las de otros usuarios](#_core_your_updates_and_the_updates_of_other_users).  
  
-   [Más información acerca de las funciones miembro Update y Delete](#_core_more_about_update_and_delete).  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si ha implementado la obtención masiva de filas, parte de la información no se aplica. Por ejemplo, no se puede llamar a la `AddNew`, **editar**, **eliminar**, y **actualización** funciones de miembro; sin embargo, puede realizar transacciones. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_how_other_operations_affect_updates"></a> Cómo afectan otras operaciones a las actualizaciones  
 Las actualizaciones se ven afectadas por las transacciones en vigor en el momento de la actualización, cerrando el conjunto de registros antes de completar una transacción y mediante el desplazamiento antes de completar una transacción.  
  
###  <a name="_core_how_transactions_affect_updates"></a> ¿Cómo afectan las transacciones a las actualizaciones  
 Más allá de comprender cómo `AddNew`, **editar**, y **eliminar** trabajo, es importante entender cómo la **BeginTrans**, **CommitTrans**, y **reversión** las funciones miembro de [CDatabase](../../mfc/reference/cdatabase-class.md) funcionan con las funciones de actualización de [CRecordset](../../mfc/reference/crecordset-class.md).  
  
 De forma predeterminada, las llamadas a `AddNew` y **editar** afectan a los datos de origen inmediatamente cuando se llama **actualización**. **Eliminar** llamadas surten efecto inmediatamente. Pero puede establecer una transacción y ejecutar un lote de este tipo de llamadas. Las actualizaciones no son permanentes hasta que los confirme. Si cambia de opinión, puede revertir la transacción en lugar de confirmarla.  
  
 Para obtener más información acerca de las transacciones, vea [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
###  <a name="_core_how_closing_the_recordset_affects_updates"></a> Cómo cerrar el conjunto de registros que afecta a las actualizaciones  
 Si cierra un conjunto de registros o su asociado `CDatabase` objeto, con una transacción en curso (no ha llamado [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) o [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)), se revierte la transacción realice una copia de forma automática (a menos que el back-end de base de datos es el motor de base de datos de Microsoft Jet).  
  
> [!CAUTION]
>  Si está utilizando el motor de base de datos de Microsoft Jet, cerrar un conjunto de registros dentro de una transacción explícita no da como resultado la liberación de ninguna de las filas modificadas o bloqueos que se colocaron hasta que se confirma o revierte la transacción explícita. Se recomienda abrir y cerrar siempre los conjuntos de registros dentro o fuera de una transacción Jet explícita.  
  
###  <a name="_core_how_scrolling_affects_updates"></a> Cómo afecta el desplazamiento a las actualizaciones  
 Cuando se [conjunto de registros: desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) en un conjunto de registros, el búfer de edición se llena con cada nuevo registro actual (el registro anterior no se almacena en primer lugar). El desplazamiento pasa por los registros que se haya eliminado previamente. Si produce un desplazamiento después un `AddNew` o **editar** llamada sin llamar a **actualización**, **CommitTrans**, o **reversión** en primer lugar, los cambios se pierden (sin ninguna advertencia para usted) como un nuevo registro se pone en el búfer de edición. El búfer de edición se llena con el registro que se desplaza, se libera el registro almacenado y se produce ningún cambio en el origen de datos. Esto se aplica a ambos `AddNew` y **editar**.  
  
##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> Las actualizaciones y las actualizaciones de otros usuarios  
 Cuando se usa un conjunto de registros para actualizar datos, sus actualizaciones afectan a otros usuarios. De forma similar, las actualizaciones de otros usuarios durante la duración del conjunto de registros le afectan.  
  
 En un entorno multiusuario, otros usuarios pueden abrir conjuntos de registros que contienen algunos de los mismos registros que seleccionó en el conjunto de registros. Los cambios en un registro antes de recuperarlo se reflejan en el conjunto de registros. Debido a conjuntos de registros dinámicos recuperan un registro cada vez que se desplaza a él, conjuntos de registros dinámicos reflejan los cambios cada vez que se desplaza a un registro. Las instantáneas de recuperan un registro de la primera vez que se desplaza a él, por lo que las instantáneas sólo reflejan los cambios que se producen antes de que se desplaza al registro inicialmente.  
  
 Los registros agregados por otros usuarios después de abrir el conjunto de registros no se muestran en el conjunto de registros, a menos que repita la consulta. Si el conjunto de registros es un conjunto de registros dinámicos, las modificaciones realizadas en los registros existentes por otros usuarios se muestran en el conjunto de registros dinámicos cuando se desplaza al registro afectado. Si el conjunto de registros es una instantánea, las modificaciones no se muestran hasta una nueva consulta de la instantánea. Si desea ver los registros agregados o eliminados por otros usuarios en una instantánea, o los registros agregados por otros usuarios en el conjunto de registros dinámicos, llame a [CRecordset:: Requery](../../mfc/reference/crecordset-class.md#requery) volver a generar el conjunto de registros. (Tenga en cuenta que las eliminaciones de otros usuarios se mostrarán en el conjunto de registros dinámicos). También puede llamar a **Requery** para ver los registros agregue, pero no para ver las eliminaciones.  
  
> [!TIP]
>  Para forzar el almacenamiento en caché de toda una instantánea a la vez, llame a `MoveLast` inmediatamente después de abrir la instantánea. A continuación, llame a **MoveFirst** para empezar a trabajar con los registros. `MoveLast` es equivalente a desplazarse por todos los registros, pero recupera todos a la vez. Sin embargo, tenga en cuenta que esto puede reducir el rendimiento y no será necesario para algunos controladores.  
  
 Los efectos de las actualizaciones en otros usuarios son similares a sus efectos depende de usted.  
  
##  <a name="_core_more_about_update_and_delete"></a> Más información acerca de Update y Delete  
 Esta sección proporciona información adicional para ayudarle a trabajar con **actualización** y **eliminar**.  
  
### <a name="update-success-and-failure"></a>Actualización correctos y erróneos  
 Si **actualización** se realiza correctamente, el `AddNew` o **editar** finaliza el modo. Para comenzar una `AddNew` o **editar** modo nuevo, llamada `AddNew` o **editar**.  
  
 Si **actualización** se produce un error (devuelve **FALSE** o produce una excepción), permanece en `AddNew` o **editar** modo, según la función llamada en último lugar. A continuación, puede hacer una de las siguientes acciones:  
  
-   Modificar un miembro de datos de campo e intente la **actualización** nuevo.  
  
-   Llame a `AddNew` para restablecer los miembros de datos de campo en Null, establezca los valores de los miembros de datos de campo y, a continuación, llame a **actualización** nuevo.  
  
-   Llame a **editar** para volver a cargar los valores que se encontraban en el conjunto de registros antes de la primera llamada a `AddNew` o **editar**, establezca los valores de los miembros de datos de campo y, a continuación, llame a **actualizar**nuevo. Después de una correcta **actualización** llamar (salvo tras un `AddNew` llamar a), los miembros de datos de campo retienen sus nuevos valores.  
  
-   Llame a **mover** (incluidos **mover** con un parámetro de **AFX_MOVE_REFRESH**, o 0), que vacía cualquiera cambia y se finaliza cualquier `AddNew` o **editar** modo en vigor.  
  
### <a name="update-and-delete"></a>Update y Delete  
 En esta sección se aplica a los **actualización** y **eliminar**.  
  
 En un **actualización** o **eliminar** operación, debe actualizarse uno y solo un registro. Dicho registro es el registro actual, que se corresponde con los valores de datos en los campos del conjunto de registros. Si por algún motivo no hay registros afectados, o más de un registro se ve afectado, se produce una excepción que contiene uno de los siguientes **RETCODE** valores:  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED**  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED**  
  
 Cuando se produzcan estas excepciones, permanece en el `AddNew` o **editar** que estaba activo cuando llama a **actualización** o **eliminar**. Estos son los escenarios más comunes en el que verá estas excepciones. Es más probable encontrar:  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED** cuando se utiliza el modo de bloqueo optimista y otro usuario ha modificado el registro de forma que impide que el marco de trabajo identificar el registro correcto para actualizar o eliminar.  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED** cuando la tabla que se va a actualizar no tiene ninguna clave principal o índice único y no tiene suficientes columnas en el conjunto de registros para identificar de forma única una fila de tabla.  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [SQL](../../data/odbc/sql.md)   
 [Excepciones: Excepciones de base de datos](../../mfc/exceptions-database-exceptions.md)