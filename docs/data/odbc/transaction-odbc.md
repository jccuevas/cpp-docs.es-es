---
title: Transacción (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
ms.openlocfilehash: 56629f8c5ff74aff4e0df589cda1e7b988fb5fd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376410"
---
# <a name="transaction-odbc"></a>Transacción (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Una transacción es una forma de agrupar o procesar lotes una serie de actualizaciones en un origen de [datos](../../data/odbc/data-source-odbc.md) para que todas se confirmen a la vez o ninguna se confirmen si se revierte la transacción. Si no utiliza una transacción, los cambios en el origen de datos se confirman automáticamente en lugar de confirmarse a petición.

> [!NOTE]
> No todos los controladores de base de datos ODBC admiten transacciones. Llame `CanTransact` a la función miembro de su [CDatabase](../../mfc/reference/cdatabase-class.md) o [CRecordset](../../mfc/reference/crecordset-class.md) objeto para determinar si el controlador admite transacciones para una base de datos determinada. Tenga `CanTransact` en cuenta que no indica si el origen de datos proporciona compatibilidad completa con transacciones. También debe `CDatabase::GetCursorCommitBehavior` llamar `CDatabase::GetCursorRollbackBehavior` `CommitTrans` y `Rollback` después y para comprobar `CRecordset` el efecto de la transacción en el objeto abierto.

Las llamadas a las `AddNew` funciones miembro y de `Edit` un `CRecordset` objeto afectan al origen de datos inmediatamente cuando se llama a `Update`. `Delete`las llamadas también surten efecto inmediatamente. Por el contrario, puede usar una transacción `Update`que `Delete`consta de varias llamadas a `CommitTrans` `AddNew`, `Edit`, , y , que se realizan pero no se confirman hasta que se llama explícitamente. Al establecer una transacción, puede ejecutar una serie de llamadas de este tipo mientras conserva la capacidad de revertirlas. Si un recurso crítico no está disponible o alguna otra condición impide que se complete toda la transacción, puede revertir la transacción en lugar de confirmarla. En ese caso, ninguno de los cambios que pertenecen a la transacción afecta al origen de datos.

> [!NOTE]
> Actualmente, `CRecordset` la clase no admite actualizaciones en el origen de datos si ha implementado la obtención masiva de filas. Esto significa que no `AddNew` `Edit`puede `Delete`realizar `Update`llamadas a , , , o . Sin embargo, puede escribir sus propias funciones para realizar actualizaciones y, a continuación, llamar a esas funciones dentro de una transacción determinada. Para obtener más información acerca de la obtención masiva de filas, vea [Conjunto de registros: obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
> Además `CDatabase` de afectar al conjunto de registros, las transacciones afectan a las instrucciones SQL que se ejecutan directamente siempre que utilice el ODBC **HDBC** asociado al objeto o un ODBC **HSTMT** basado en ese **HDBC**.

Las transacciones son especialmente útiles cuando tiene varios registros que deben actualizarse simultáneamente. En este caso, desea evitar una transacción semicompletada, como podría ocurrir si se produce una excepción antes de que se realizara la última actualización. La agrupación de estas actualizaciones en una transacción permite una recuperación (reversión) de los cambios y devuelve los registros al estado de pretransacción. Por ejemplo, si un banco transfiere dinero de la cuenta A a la cuenta B, tanto el retiro de A como el depósito a B deben tener éxito para procesar los fondos correctamente o toda la transacción debe fallar.

En las clases de base `CDatabase` de datos, se realizan transacciones a través de objetos. Un `CDatabase` objeto representa una conexión a un origen de datos `CDatabase` y uno o varios conjuntos de registros asociados a ese objeto funcionan en tablas de la base de datos a través de funciones miembro de conjunto de registros.

> [!NOTE]
> Solo se admite un nivel de transacciones. No puede anidar transacciones ni una transacción puede abarcar varios objetos de base de datos.

Los temas siguientes proporcionan más información sobre cómo se realizan las transacciones:

- [Transacción: Realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Consulte también

[Conectividad de base de datos abierta (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
