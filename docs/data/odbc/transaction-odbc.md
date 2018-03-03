---
title: "Transacción (ODBC) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2816e1cfe3c62fecede5c909bc1593779aa90d54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-odbc"></a>Transacción (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Una transacción es una forma Agrupar, o por lotes, una serie de actualizaciones para un [origen de datos](../../data/odbc/data-source-odbc.md) para que se confirmen todas a la vez o no se confirmará ninguno si se deshace la transacción. Si no utiliza una transacción, los cambios en el origen de datos se confirman automáticamente en lugar de confirmarse a petición.  
  
> [!NOTE]
>  No todos los controladores de base de datos ODBC admiten transacciones. Llame a la `CanTransact` función miembro de la [CDatabase](../../mfc/reference/cdatabase-class.md) o [CRecordset](../../mfc/reference/crecordset-class.md) objeto para determinar si el controlador admite las transacciones para una base de datos. Tenga en cuenta que `CanTransact` no indica si el origen de datos proporciona total compatibilidad con transacciones. También debe llamar a `CDatabase::GetCursorCommitBehavior` y `CDatabase::GetCursorRollbackBehavior` después **CommitTrans** y **reversión** para comprobar el efecto de la transacción al abrir `CRecordset` objeto.  
  
 Llamadas a la `AddNew` y **editar** las funciones miembro de un `CRecordset` objeto afectan a los datos de origen inmediatamente cuando se llama **actualización**. **Eliminar** llamadas también surten efecto inmediatamente. En cambio, puede utilizar una transacción que consta de varias llamadas a `AddNew`, **editar**, **actualización**, y **eliminar**, que se ejecutan pero no se confirman hasta que se llama a **CommitTrans** explícitamente. Mediante el establecimiento de una transacción, puede ejecutar una serie de llamadas de ese tipo conservando la capacidad de revertir a ellos. Si no está disponible un recurso crítico o cualquier otra circunstancia que impida que toda la transacción se complete, puede revertir la transacción en lugar de confirmarla. En ese caso, ninguno de los cambios que pertenecen a la transacción afectan al origen de datos.  
  
> [!NOTE]
>  Actualmente, la clase `CRecordset` no admite actualizaciones al origen de datos si ha implementado la obtención masiva de filas. Esto significa que no se puede realizar llamadas a `AddNew`, **editar**, **eliminar**, o **actualización**. Sin embargo, puede escribir sus propias funciones para realizar actualizaciones y, a continuación, llamar a esas funciones dentro de una transacción determinada. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Además de influir en el conjunto de registros, las transacciones afectan a las instrucciones SQL que ejecutan directamente como usar el SDK de ODBC **HDBC** asociada a su `CDatabase` objeto o un ODBC **HSTMT** tomando como base que **HDBC**.  
  
 Las transacciones son especialmente útiles cuando hay varios registros que deben actualizarse al mismo tiempo. En este caso, conviene evitar una transacción parcialmente completada, como puede suceder si se produce una excepción antes de que se realizó la última actualización. Agrupar tales actualizaciones en una transacción permite una recuperación (reversión) de los cambios y devuelve los registros en el estado previo. Por ejemplo, si un banco transfiere dinero de la cuenta A la cuenta B, tanto la retirada de A y el depósito en B debe tener éxito para los fondos se procesen correctamente o la transacción entera debe cancelarse.  
  
 En las clases de base de datos, realizar las transacciones a través de `CDatabase` objetos. A `CDatabase` objeto representa una conexión a un origen de datos y uno o varios conjuntos de registros asociados a ese `CDatabase` objeto funcionan en tablas de la base de datos a través de funciones miembro de conjunto de registros.  
  
> [!NOTE]
>  Se admite solo un nivel de transacciones. No se pueden anidar transacciones ni puede abarcar una transacción varios objetos de base de datos.  
  
 Los temas siguientes proporcionan más información sobre cómo se deben realizar las transacciones:  
  
-   [Transacción: Realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
-   [Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## <a name="see-also"></a>Vea también  
 [Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)