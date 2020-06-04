---
title: Admitir transacciones en OLE DB
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
ms.openlocfilehash: e7ec4f69b4bba497446c94afb94cb5a1d648f7c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209561"
---
# <a name="supporting-transactions-in-ole-db"></a>Admitir transacciones en OLE DB

Una [transacción](../../data/transactions-mfc-data-access.md) es una manera de agrupar, o procesar por lotes, una serie de actualizaciones en un origen de datos de modo que todas se realicen correctamente y se confirmen a la vez o (si se produce un error en cualquiera de ellas) no se confirmen y se revierta toda la transacción. Este proceso garantiza la integridad del resultado en el origen de datos.

OLE DB admite transacciones con los tres métodos siguientes:

- [ITransactionLocal:: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction:: commit](/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction:: ABORT](/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>Relación de sesiones y transacciones

Un único objeto de origen de datos puede crear uno o varios objetos de sesión, cada uno de los cuales puede estar dentro o fuera del ámbito de una transacción en un momento dado.

Cuando una sesión no entra en una transacción, todo el trabajo realizado dentro de esa sesión en el almacén de datos se confirma inmediatamente en cada llamada al método. (Esto se conoce a veces como modo de confirmación automática o modo implícito).

Cuando una sesión entra en una transacción, todo el trabajo realizado dentro de esa sesión en el almacén de datos forma parte de esa transacción y se confirma o anula como una sola unidad. (Esto se conoce a veces como modo de confirmación manual).

La compatibilidad con transacciones es específica del proveedor. Si el proveedor que está usando admite transacciones, un objeto de sesión que admita `ITransaction` y `ITransactionLocal` puede especificar una transacción (no anidada). La clase de plantillas OLE DB [CSession](../../data/oledb/csession-class.md) es compatible con estas interfaces y es la manera recomendada de implementar la C++compatibilidad con transacciones en visual.

## <a name="starting-and-ending-the-transaction"></a>Inicio y finalización de la transacción

Llame a los métodos `StartTransaction`, `Commit`y `Abort` en el objeto de conjunto de filas en el consumidor.

La llamada a `ITransactionLocal::StartTransaction` inicia una nueva transacción local. Al iniciar la transacción, los cambios que hayan solicitado las operaciones posteriores no se aplican al almacén de datos hasta que se confirme la transacción.

La llamada a `ITransaction::Commit` o `ITransaction::Abort` finaliza la transacción. `Commit` hace que todos los cambios dentro del ámbito de la transacción se apliquen al almacén de datos. `Abort` provoca que se cancelen todos los cambios dentro del ámbito de la transacción y que el almacén de datos se queda en el estado que tenía antes de que se iniciara la transacción.

## <a name="nested-transactions"></a>Transacciones anidadas

Una [transacción anidada](/previous-versions/windows/desktop/ms716985(v=vs.85)) se produce cuando se inicia una nueva transacción local cuando ya existe una transacción activa en la sesión. La nueva transacción se inicia como una transacción anidada por debajo de la transacción actual. Si el proveedor no admite transacciones anidadas, al llamar a `StartTransaction` cuando ya hay una transacción activa en la sesión, se devuelve XACT_E_XTIONEXISTS.

## <a name="distributed-transactions"></a>Transacciones distribuidas

Una transacción distribuida es una transacción que actualiza datos distribuidos. es decir, datos en más de un sistema informático en red. Si desea admitir transacciones a través de un sistema distribuido, debe usar el .NET Framework en lugar de la compatibilidad con transacciones de OLE DB.

## <a name="see-also"></a>Consulte también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)
