---
title: Admitir transacciones en OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 76dc4cb86601be714e7ca1d442eb904d016e877b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102793"
---
# <a name="supporting-transactions-in-ole-db"></a>Admitir transacciones en OLE DB

Un [transacciones](../../data/transactions-mfc-data-access.md) es una forma Agrupar, o por lotes, una serie de actualizaciones a un origen de datos para que todo se ejecuta correctamente y se confirman al mismo tiempo o (si alguna de ellos se produce un error) ninguno se confirman y se revierte la transacción entera. Este proceso garantiza la integridad del resultado en el origen de datos.  
  
OLE DB admite las transacciones con los tres métodos siguientes:  
  
- [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786\(v=vs.85\))  
  
- [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008\(v=vs.85\))  
  
- [ITransaction:: Abort](/previous-versions/windows/desktop/ms709833\(v=vs.85\))  
  
## <a name="relationship-of-sessions-and-transactions"></a>Relación de sesiones y transacciones  

Un objeto de origen de datos solo puede crear uno o varios objetos de sesión, cada uno de los cuales puede encontrarse dentro o fuera del ámbito de una transacción en un momento dado.  
  
Cuando una sesión no entran en una transacción, todo el trabajo realizado dentro de esa sesión en el almacén de datos se confirma inmediatamente en cada llamada al método. (Esto se denomina a veces el modo de confirmación automática o implícitas.)  
  
Cuando una sesión entra en una transacción, todo el trabajo realizado dentro de esa sesión en el almacén de datos forma parte de esa transacción y se confirma o anular como una sola unidad. (Esto se conoce a veces como modo de confirmación manual.)  
  
Compatibilidad con transacciones es específica del proveedor. Si el proveedor usa admite transacciones, un objeto de sesión que admita `ITransaction` y `ITransactionLocal` puede introducir una sencilla (es decir, no anidadas) transacciones. La clase de plantillas OLE DB [CSession](../../data/oledb/csession-class.md) admite estas interfaces y es la manera recomendada para implementar la compatibilidad con transacciones en Visual C++.  
  
## <a name="starting-and-ending-the-transaction"></a>Inicio y finalización de la transacción  

Se llama a la `StartTransaction`, `Commit`, y `Abort` métodos del objeto de conjunto de filas en el consumidor.  
  
Una llamada a `ITransactionLocal::StartTransaction` inicia una nueva transacción local. Cuando se inicia la transacción, los cambios exigidos por las operaciones posteriores no se aplican realmente al almacén de datos hasta que se confirme la transacción.  
  
Una llamada a `ITransaction::Commit` o `ITransaction::Abort` finaliza la transacción. `Commit` hace que todos los cambios dentro del ámbito de la transacción que se aplican al almacén de datos. `Abort` hace que todos los cambios dentro del ámbito de la transacción se cancela y el almacén de datos se deja en el estado tenía antes de comenzar la transacción.  
  
## <a name="nested-transactions"></a>Transacciones anidadas  

Un [anidar transacciones](/previous-versions/windows/desktop/ms716985\(v=vs.85\)) se produce cuando se inicia una nueva transacción local cuando una transacción activa ya existe en la sesión. La nueva transacción se inicia como una transacción anidada bajo la transacción actual. Si el proveedor no admite transacciones anidadas, la llamada a `StartTransaction` cuando ya hay una transacción activa en la sesión, devuelve XACT_E_XTIONEXISTS.  
  
## <a name="distributed-transactions"></a>Transacciones distribuidas  

Una transacción distribuida es una transacción que actualiza datos distribuidos; es decir, los datos en más de un equipo en red. Si desea admitir transacciones en un sistema distribuido, debe usar .NET Framework en lugar de la compatibilidad con transacciones de OLE DB.  
  
## <a name="see-also"></a>Vea también  

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)