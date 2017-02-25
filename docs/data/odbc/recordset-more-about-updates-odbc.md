---
title: "Conjunto de registros: Informaci&#243;n adicional sobre las actualizaciones (ODBC) | Microsoft Docs"
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
  - "entornos multiusuario, actualizaciones de conjuntos de registros"
  - "conjuntos de registros ODBC, actualizar"
  - "registros, actualizar"
  - "conjuntos de registros, actualizar"
  - "desplazarse, actualizaciones de conjuntos de registros"
  - "transacciones, actualizar conjuntos de registros"
  - "actualizar conjuntos de registros"
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Conjunto de registros: Informaci&#243;n adicional sobre las actualizaciones (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 En este tema se explica:  
  
-   [Cómo afectan otras operaciones, como las transacciones, a las actualizaciones](#_core_how_transactions_affect_updates).  
  
-   [Sus actualizaciones y las de otros usuarios](#_core_your_updates_and_the_updates_of_other_users).  
  
-   [Más acerca de las funciones miembro Update y Delete](#_core_more_about_update_and_delete).  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si está implementada la obtención de filas masiva, parte de esta información no es aplicable.  Por ejemplo, no es posible llamar a las funciones miembro `AddNew`, **Edit**, **Delete** y **Update**; sin embargo, se pueden realizar transacciones.  Para obtener más información sobre la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_how_other_operations_affect_updates"></a> Cómo afectan otras operaciones a las actualizaciones  
 Sus propias actualizaciones se ven afectadas por las transacciones activas en el momento de la actualización, cerrando el conjunto de registros antes de completar una transacción y desplazando la posición en el conjunto de registros antes de completar la transacción.  
  
###  <a name="_core_how_transactions_affect_updates"></a> Cómo afectan las transacciones a las actualizaciones  
 Además de comprender el funcionamiento de `AddNew`, **Edit** y **Delete**, es importante entender cómo actúan las funciones miembro **BeginTrans**, **CommitTrans** y **Rollback** de [CDatabase](../../mfc/reference/cdatabase-class.md) con las funciones de actualización de [CRecordset](../../mfc/reference/crecordset-class.md).  
  
 De forma predeterminada, las llamadas a `AddNew` y **Edit** afectan inmediatamente al origen de datos cuando se llama a **Update**.  Las llamadas a **Delete** surten efecto de inmediato.  Pero se puede crear una transacción y ejecutar un lote de este tipo de llamadas.  Las actualizaciones no son permanentes hasta que se confirman.  Si cambia de opinión, puede revertir *\(roll back\)* la transacción en lugar de confirmarla.  
  
 Para obtener más información sobre transacciones, consulte [Transacción \(ODBC\)](../../data/odbc/transaction-odbc.md).  
  
###  <a name="_core_how_closing_the_recordset_affects_updates"></a> Cómo afecta el cierre del conjunto de registros a las actualizaciones  
 Al cerrar un conjunto de registros o su objeto `CDatabase` asociado con una transacción en progreso \(es decir, sin haber llamado a [CDatabase::CommitTrans](../Topic/CDatabase::CommitTrans.md) ni a [CDatabase::Rollback](../Topic/CDatabase::Rollback.md)\), ésta se revierte automáticamente, a menos que el back\-end de la base de datos sea el motor de bases de datos Microsoft Jet.  
  
> [!CAUTION]
>  Si usa el motor de base de datos Jet de Microsoft, cerrar un conjunto de registros dentro de una transacción explícita no da como resultado la liberación de ninguna de las filas modificadas ni de los bloqueos aplicados hasta que se confirme o revierta la transacción explícita.  Se recomienda abrir y cerrar siempre los conjuntos de registros dentro o fuera de una transacción Jet explícita.  
  
###  <a name="_core_how_scrolling_affects_updates"></a> Cómo afecta el desplazamiento a las actualizaciones  
 Al hacer [Conjunto de registros: Desplazamiento \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md) por un conjunto de registros, el búfer de edición se llena con cada nuevo registro actual \(el registro anterior no se almacena en primer lugar\).  El desplazamiento pasa por alto los registros previamente eliminados.  Si se produce un desplazamiento después de una llamada a `AddNew` o **Edit** sin llamar antes a **Update**, **CommitTrans** o **Rollback**, se pierden los cambios \(sin advertencia previa\) cuando se agrega un nuevo registro al búfer de edición.  El búfer de edición se llena con el registro al que se efectuó el desplazamiento, se libera el registro almacenado y no se produce ningún cambio en el origen de datos.  Esto se aplica tanto a `AddNew` como a **Edit**.  
  
##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> Sus actualizaciones y las actualizaciones de otros usuarios  
 Al utilizar un conjunto de registros para actualizar datos, sus actualizaciones afectan a otros usuarios.  De forma similar, las actualizaciones de los demás usuarios durante la existencia del conjunto de registros le afectan.  
  
 En un entorno multiusuario, los demás usuarios pueden abrir conjuntos de registros que contengan algunos de los mismos registros que seleccionó en el conjunto de registros.  Los cambios realizados en un registro antes de recuperarlo se reflejan en el conjunto de registros.  Puesto que los conjuntos de registros dinámicos recuperan un registro cada vez que se desplaza a él, reflejan los cambios cada vez que se desplace a un registro.  Las instantáneas, por el contrario, recuperan un registro la primera vez que se desplaza a su posición, por lo que sólo reflejan los cambios realizados antes de desplazarse hasta él por primera vez.  
  
 Los registros agregados por otros usuarios después de abrir el conjunto de registros no aparecen en él hasta realizar una nueva consulta.  Si el conjunto de registros es de tipo dinámico, las modificaciones de registros existentes efectuadas por otros usuarios no aparecen en él al desplazarse al registro afectado.  Si el conjunto de registros es una instantánea, las modificaciones no se reflejan hasta realizar una nueva consulta al mismo.  Si desea ver los registros agregados o eliminados por otros usuarios en una instantánea, o los registros agregados por otros usuarios en un conjunto de registros dinámicos, llame a [CRecordset::Requery](../Topic/CRecordset::Requery.md) para recompilar el conjunto de registros. \(Observe que las eliminaciones de otros usuarios no aparecen en el conjunto de registros dinámicos.\) También se puede llamar a **Requery** para ver los registros que se agregan, pero no para ver las eliminaciones.  
  
> [!TIP]
>  Para forzar el almacenamiento en caché de una instantánea completa con rapidez, llame a `MoveLast` inmediatamente después de abrir la instantánea.  A continuación, llame a **MoveFirst** para empezar a trabajar con los registros.  `MoveLast` es equivalente a desplazarse por todos los registros, pero los recupera todos a la vez.  Observe, sin embargo, que se puede reducir el rendimiento y quizá no sea necesario para algunos controladores.  
  
 Los efectos de las actualizaciones que realiza en los conjuntos de registros de otros usuarios son similares a los que tienen las actualizaciones de estos últimos en su propio conjunto de registros.  
  
##  <a name="_core_more_about_update_and_delete"></a> Más sobre Update y Delete  
 Esta sección proporciona información adicional para ayudarle a trabajar con **Update** y **Delete**.  
  
### Ejecución de Update correcta o errónea  
 Si **Update** se ejecuta correctamente, termina el modo `AddNew` o **Edit**.  Para comenzar un modo `AddNew` o **Edit** de nuevo, llame a las funciones del mismo nombre.  
  
 Si se produce un error en **Update** \(devuelve **FALSE** o produce una excepción\), el modo `AddNew` o **Edit** continúa activo, según la función llamada en último lugar.  A continuación se puede dar uno de los siguientes pasos:  
  
-   Modifique un miembro de datos de campo e intente ejecutar **Update** de nuevo.  
  
-   Llame a `AddNew` para restablecer los miembros de datos del campo en Null, establezca los valores de los miembros de datos del campo y llame de nuevo a **Update**.  
  
-   Llame a **Edit** para volver a cargar los valores existentes en el conjunto de registros antes de la primera llamada a `AddNew` o **Edit**, establezca los valores de los miembros de datos de campo y, a continuación, vuelva a llamar a **Update**.  Después de una llamada correcta a **Update** \(excepto después de una llamada a `AddNew`\), los miembros de datos de campo retienen sus nuevos valores.  
  
-   Llame a **Move** \(incluyendo a **Move** con un parámetro de **AFX\_MOVE\_REFRESH** ó 0\), que vuelca los cambios realizados y termina cualquier modo `AddNew` o **Edit** que haya en vigor.  
  
### Update y Delete  
 Esta sección se aplica tanto a **Update** como a **Delete**.  
  
 En una operación **Update** o **Delete**, sólo debe actualizarse un registro.  Dicho registro es el registro actual, que corresponde a los valores de datos asignados a los campos del conjunto de registros.  Si por algún motivo no hay registros afectados, o hay más de un registro afectado, se produce una excepción que contiene uno de los siguientes valores **RETCODE**:  
  
-   **AFX\_SQL\_ERROR\_NO\_ROWS\_AFFECTED**  
  
-   **AFX\_SQL\_ERROR\_MULTIPLE\_ROWS\_AFFECTED**  
  
 Al producirse estas excepciones, se continúa en el modo `AddNew` o **Edit** que estaba activo al llamar a **Update** o **Delete**.  A continuación se enumeran los escenarios de uso más comunes para estas excepciones.  Con frecuencia verá:  
  
-   **AFX\_SQL\_ERROR\_NO\_ROWS\_AFFECTED** cuando utilice el modo de bloqueo optimista y otro usuario haya modificado el registro de forma que impida al marco de trabajo identificar el registro correcto para actualizar o eliminar.  
  
-   **AFX\_SQL\_ERROR\_MULTIPLE\_ROWS\_AFFECTED** cuando la tabla que está actualizando no posea clave principal o índice único y no haya suficientes columnas en el conjunto de registros para identificar de forma única una fila de tabla.  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Cómo se seleccionan los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [SQL](../../data/odbc/sql.md)   
 [Excepciones: Excepciones de base de datos](../../mfc/exceptions-database-exceptions.md)