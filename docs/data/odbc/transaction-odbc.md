---
title: Transacción (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ba77eb5289dcd2bd169b85fe9a595c231a86cf4c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056183"
---
# <a name="transaction-odbc"></a>Transacción (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Una transacción es una forma Agrupar, o por lotes, una serie de actualizaciones para un [origen de datos](../../data/odbc/data-source-odbc.md) para que se confirmen todas a la vez o no se confirme si se deshace la transacción. Si no usa una transacción, los cambios realizados en el origen de datos se confirman automáticamente en lugar de confirmarse a petición.

> [!NOTE]
>  No todos los controladores de base de datos ODBC admiten transacciones. Llame a la `CanTransact` función miembro de su [CDatabase](../../mfc/reference/cdatabase-class.md) o [CRecordset](../../mfc/reference/crecordset-class.md) objeto para determinar si el controlador admite las transacciones para una base de datos. Tenga en cuenta que `CanTransact` no indica si el origen de datos proporciona total compatibilidad con transacciones. También debe llamar a `CDatabase::GetCursorCommitBehavior` y `CDatabase::GetCursorRollbackBehavior` después `CommitTrans` y `Rollback` para comprobar el efecto de la transacción en la apertura `CRecordset` objeto.

Las llamadas a la `AddNew` y `Edit` funciones miembro de un `CRecordset` efecto inmediatamente cuando se llama del origen de datos de objeto `Update`. `Delete` llamadas también surten efecto inmediatamente. En cambio, puede usar una transacción que consta de varias llamadas a `AddNew`, `Edit`, `Update`, y `Delete`, que se ejecutan pero no se confirman hasta que llame a `CommitTrans` explícitamente. Mediante el establecimiento de una transacción, puede ejecutar una serie de llamadas de ese tipo conservando la capacidad de revertir a ellos. Si no está disponible un recurso crítico o alguna otra condición impide que se complete toda la transacción, puede revertir la transacción en lugar de confirmarla. En ese caso, ninguno de los cambios que pertenecen a la transacción afectan al origen de datos.

> [!NOTE]
>  Actualmente, la clase `CRecordset` no admite actualizaciones al origen de datos si se ha implementado la obtención masiva de filas. Esto significa que no se puede realizar llamadas a `AddNew`, `Edit`, `Delete`, o `Update`. Sin embargo, puede escribir sus propias funciones para realizar actualizaciones y, a continuación, llamar a esas funciones dentro de una transacción determinada. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Además de que afecte a su conjunto de registros, las transacciones afectan a instrucciones SQL que ejecutan directamente como usar ODBC **HDBC** asociada con su `CDatabase` objeto o un ODBC **HSTMT** según que **HDBC**.

Las transacciones son especialmente útiles cuando hay varios registros que deben actualizarse al mismo tiempo. En este caso, desea evitar una transacción parcialmente completada, como puede suceder si se produjo una excepción antes de que se realizó la última actualización. Agrupar tales actualizaciones en una transacción permite una recuperación (reversión) de los cambios y devuelve los registros al estado previo. Por ejemplo, si un banco transfiere dinero de la cuenta a la cuenta B, tanto la retirada de A y el depósito en B debe realizarse correctamente para los fondos se procesen correctamente o debe producir un error en toda la transacción.

En las clases de base de datos, llevará a cabo las transacciones a través de `CDatabase` objetos. Un `CDatabase` objeto representa una conexión a un origen de datos y uno o varios conjuntos de registros asociados con dicha `CDatabase` objeto operan en las tablas de la base de datos a través de las funciones de miembro del conjunto de registros.

> [!NOTE]
>  Se admite sólo un nivel de transacciones. No se pueden anidar transacciones ni pueden abarcar varios objetos de base de datos.

Los temas siguientes proporcionan más información acerca de cómo se realizan transacciones:

- [Transacción: Realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Vea también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)