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
ms.openlocfilehash: 3c71200e39641a69443599e0445f89f469aceeda
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038753"
---
# <a name="supporting-transactions-in-ole-db"></a>Admitir transacciones en OLE DB

Un [transacciones](../../data/transactions-mfc-data-access.md) es una forma Agrupar, o por lotes, una serie de actualizaciones a un origen de datos para que todo se ejecuta correctamente y se confirman al mismo tiempo o (si alguna de ellos se produce un error) ninguno se confirman y se revierte la transacción entera. Este proceso garantiza la integridad del resultado en el origen de datos.

OLE DB admite las transacciones con los tres métodos siguientes:

- [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction::Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction::Abort](/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>Relación de sesiones y transacciones

Un objeto de origen de datos solo puede crear uno o varios objetos de sesión, cada uno de los cuales puede encontrarse dentro o fuera del ámbito de una transacción en un momento dado.

Cuando una sesión no entran en una transacción, todo el trabajo realizado dentro de esa sesión en el almacén de datos se confirma inmediatamente en cada llamada al método. (Esto se denomina a veces el modo de confirmación automática o implícitas.)

Cuando una sesión entra en una transacción, todo el trabajo realizado dentro de esa sesión en el almacén de datos forma parte de esa transacción y se confirma o anular como una sola unidad. (Esto se conoce a veces como modo de confirmación manual.)

Compatibilidad con transacciones es específica del proveedor. Si el proveedor que está usando admite transacciones, un objeto de sesión que admita `ITransaction` y `ITransactionLocal` puede anotar una transacción (no anidado). La clase de plantillas OLE DB [CSession](../../data/oledb/csession-class.md) admite estas interfaces y es la manera recomendada para implementar la compatibilidad con transacciones en Visual C++.

## <a name="starting-and-ending-the-transaction"></a>Inicio y finalización de la transacción

Se llama a la `StartTransaction`, `Commit`, y `Abort` métodos del objeto de conjunto de filas en el consumidor.

Una llamada a `ITransactionLocal::StartTransaction` inicia una nueva transacción local. Cuando se inicia la transacción, los cambios exigidos por las operaciones posteriores no se aplican al almacén de datos hasta que se confirme la transacción.

Una llamada a `ITransaction::Commit` o `ITransaction::Abort` finaliza la transacción. `Commit` hace que todos los cambios dentro del ámbito de la transacción que se aplican al almacén de datos. `Abort` hace que todos los cambios dentro del ámbito de la transacción se cancela y el almacén de datos se deja en el estado tenía antes de comenzar la transacción.

## <a name="nested-transactions"></a>Transacciones anidadas

Un [anidar transacciones](/previous-versions/windows/desktop/ms716985(v=vs.85)) se produce cuando se inicia una nueva transacción local cuando una transacción activa ya existe en la sesión. La nueva transacción se inicia como una transacción anidada bajo la transacción actual. Si el proveedor no admite transacciones anidadas, la llamada a `StartTransaction` cuando ya hay una transacción activa en la sesión, devuelve XACT_E_XTIONEXISTS.

## <a name="distributed-transactions"></a>Transacciones distribuidas

Una transacción distribuida es una transacción que actualiza datos distribuidos; es decir, los datos en más de un equipo en red. Si desea admitir transacciones en un sistema distribuido, debe usar .NET Framework en lugar de la compatibilidad con transacciones de OLE DB.

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)