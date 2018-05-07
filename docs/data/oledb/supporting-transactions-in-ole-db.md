---
title: Admitir transacciones en OLE DB | Documentos de Microsoft
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
ms.openlocfilehash: ecd5b7274e62508289a83d6c0420d5f76e239e4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="supporting-transactions-in-ole-db"></a>Admitir transacciones en OLE DB
A [transacciones](../../data/transactions-mfc-data-access.md) es una forma Agrupar, o por lotes, una serie de actualizaciones a un origen de datos para que todas correctamente y se confirman al mismo tiempo o (si alguna de ellos se produce un error) no se confirmará ninguno y se revierte la transacción entera. Este proceso garantiza la integridad del resultado en el origen de datos.  
  
 OLE DB admite transacciones con los tres métodos siguientes:  
  
-   [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx)  
  
-   [ITransaction:: Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx)  
  
-   [ITransaction:: Abort](https://msdn.microsoft.com/en-us/library/ms709833.aspx)  
  
## <a name="relationship-of-sessions-and-transactions"></a>Relación de sesiones y transacciones  
 Un objeto de origen de datos solo puede crear uno o varios objetos de sesión, cada uno de los cuales puede encontrarse dentro o fuera del ámbito de una transacción en un momento dado.  
  
 Cuando una sesión no entra en una transacción, todo el trabajo realizado dentro de esa sesión en el almacén de datos se confirma inmediatamente en cada llamada al método. (Esto se conoce a veces como modo de confirmación automática o implícitas.)  
  
 Cuando una sesión entra en una transacción, todo el trabajo realizado dentro de esa sesión en el almacén de datos forma parte de esa transacción y se confirma o anula como una sola unidad. (Esto se conoce a veces como modo de confirmación manual.)  
  
 Compatibilidad con transacciones es específica del proveedor. Si el proveedor usa admite transacciones, un objeto de sesión que admita **ITransaction** y **ITransactionLocal** puede escribir una sencilla (es decir, no anidada) transacciones. La clase de plantillas OLE DB [CSession](../../data/oledb/csession-class.md) es compatible con estas interfaces y es la manera recomendada para implementar la compatibilidad con transacciones en Visual C++.  
  
## <a name="starting-and-ending-the-transaction"></a>Iniciar y finalizar la transacción  
 Se llama a la `StartTransaction`, **confirmar**, y **anular** métodos en el objeto de conjunto de filas en el consumidor.  
  
 Al llamar a **ITransactionLocal:: StartTransaction** inicia una nueva transacción local. Cuando se inicia la transacción, los cambios forzados por sucesivas operaciones no se aplican realmente al almacén de datos hasta que se confirma la transacción.  
  
 Al llamar a **ITransaction:: Commit** o **ITransaction:: Abort** finaliza la transacción. **Confirmar** hace que todos los cambios en el ámbito de la transacción que se va a aplicarse al almacén de datos. **Anular** hace todos los cambios dentro del ámbito de la transacción se puede cancelar y el almacén de datos quede en el estado tenía antes de comenzar la transacción.  
  
## <a name="nested-transactions"></a>Transacciones anidadas  
 A [anidar transacciones](https://msdn.microsoft.com/en-us/library/ms716985.aspx) se produce cuando se inicia una nueva transacción local cuando una transacción activa ya existe en la sesión. La nueva transacción se inicia como una transacción anidada bajo la transacción actual. Si el proveedor no admite transacciones anidadas, al llamar a `StartTransaction` cuando ya hay una transacción activa en la sesión devuelve **XACT_E_XTIONEXISTS**.  
  
## <a name="distributed-transactions"></a>Transacciones distribuidas  
 Una transacción distribuida es una transacción que actualiza datos distribuidos; es decir, datos en más de un sistema de equipo de la red. Si desea admitir transacciones en un sistema distribuido, debe utilizar .NET Framework en lugar de la compatibilidad con transacciones de OLE DB.  
  
## <a name="see-also"></a>Vea también  
 [Usar descriptores de acceso](../../data/oledb/using-accessors.md)