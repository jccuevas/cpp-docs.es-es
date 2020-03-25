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
ms.openlocfilehash: 49fc0e244dd4f63bd7a69d963ff2a9fbc00ddb6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212607"
---
# <a name="transaction-odbc"></a>Transacción (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Una transacción es una manera de agrupar, o procesar por lotes, una serie de actualizaciones en un [origen de datos](../../data/odbc/data-source-odbc.md) para que todas se confirmen a la vez o no se confirmen si se revierte la transacción. Si no utiliza una transacción, los cambios en el origen de datos se confirman automáticamente en lugar de confirmarse a petición.

> [!NOTE]
>  No todos los controladores de base de datos ODBC admiten transacciones. Llame a la función miembro `CanTransact` del objeto [CDatabase](../../mfc/reference/cdatabase-class.md) o [CRecordset](../../mfc/reference/crecordset-class.md) para determinar si el controlador admite transacciones para una base de datos determinada. Tenga en cuenta que `CanTransact` no indica si el origen de datos proporciona compatibilidad total con las transacciones. También debe llamar a `CDatabase::GetCursorCommitBehavior` y `CDatabase::GetCursorRollbackBehavior` después de `CommitTrans` y `Rollback` para comprobar el efecto de la transacción en el objeto de `CRecordset` abierto.

Las llamadas a las funciones miembro `AddNew` y `Edit` de un objeto `CRecordset` afectan al origen de datos inmediatamente cuando se llama a `Update`. las llamadas `Delete` también surten efecto inmediatamente. Por el contrario, puede usar una transacción que consta de varias llamadas a `AddNew`, `Edit`, `Update`y `Delete`, que se realizan pero no se confirman hasta que se llama a `CommitTrans` explícitamente. Mediante el establecimiento de una transacción, puede ejecutar una serie de llamadas de este tipo a la vez que conserva la capacidad de revertirla. Si un recurso crítico no está disponible o alguna otra condición impide que se complete toda la transacción, puede revertir la transacción en lugar de confirmarla. En ese caso, ninguno de los cambios que pertenecen a la transacción afecta al origen de datos.

> [!NOTE]
>  Actualmente, la clase `CRecordset` no admite actualizaciones en el origen de datos si se ha implementado la obtención masiva de filas. Esto significa que no puede realizar llamadas a `AddNew`, `Edit`, `Delete`o `Update`. Sin embargo, puede escribir funciones propias para realizar actualizaciones y, a continuación, llamar a esas funciones dentro de una transacción determinada. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Además de afectar al conjunto de registros, las transacciones afectan a las instrucciones SQL que se ejecutan directamente siempre que se use el valor de **hdbc** de ODBC asociado con el objeto de `CDatabase` o un **HSTMT** de ODBC basado en ese **hdbc**.

Las transacciones son especialmente útiles cuando se tienen varios registros que se deben actualizar simultáneamente. En este caso, desea evitar una transacción de medio completado, como puede ocurrir si se produjo una excepción antes de que se realizara la última actualización. La agrupación de estas actualizaciones en una transacción permite una recuperación (reversión) de los cambios y devuelve los registros al estado anterior a la transacción. Por ejemplo, si un Banco transfiere dinero de la cuenta a a la cuenta B, la retirada de un y el depósito a B deben tener éxito para procesar los fondos correctamente o se debe producir un error en toda la transacción.

En las clases de base de datos, las transacciones se realizan a través de objetos de `CDatabase`. Un objeto `CDatabase` representa una conexión a un origen de datos y uno o más conjuntos de registros asociados a ese objeto `CDatabase` operan en tablas de la base de datos a través de funciones miembro de conjunto de registros.

> [!NOTE]
>  Solo se admite un nivel de transacciones. No se pueden anidar transacciones ni una transacción puede abarcar varios objetos de base de datos.

En los temas siguientes se proporciona más información acerca de cómo se realizan las transacciones:

- [Transacción: Realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Consulte también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
