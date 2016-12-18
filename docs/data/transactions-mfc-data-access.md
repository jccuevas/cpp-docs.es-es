---
title: "Transacciones (acceso a datos MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bases de datos [C++], transacciones"
  - "transacciones [C++]"
  - "transacciones [C++], compatibilidad"
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Transacciones (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El concepto de transacción se desarrolló para abordar los casos en que el estado resultante de la base de datos depende del éxito total de una serie de operaciones.  Esto podría suceder debido a que las operaciones sucesivas pueden modificar el resultado de las operaciones anteriores.  En estos casos, si se produce un error en una operación, el estado resultante puede ser indeterminado.  
  
 Para resolver este problema, las transacciones agrupan una serie de operaciones de tal forma que puede garantizarse la integridad del resultado final.  Todas las operaciones deben tener éxito y confirmarse \(es decir, escribirse en la base de datos\); de lo contrario, se produce un error en toda la transacción.  La cancelación de la transacción se denomina reversión.  La reversión permite una recuperación de los cambios y devuelve la base de datos al estado previo a la transacción.  
  
 Por ejemplo, en una transacción bancaria automatizada, si transfiere dinero de la cuenta A a la cuenta B, la retirada de A y el depósito en B deben tener éxito para que los fondos se procesen correctamente; de lo contrario, la transacción producirá un error.  
  
 Una transacción debe tener las propiedades ACID, que representan lo siguiente:  
  
-   **Atomicidad** Una transacción constituye una unidad atómica de trabajo y se ejecuta exactamente una sola vez; o se realiza el trabajo al completo, o nada en absoluto.  
  
-   **Coherencia** Una transacción mantiene la coherencia de los datos, pues transforma un estado coherente de datos en otro estado coherente de datos.  Los datos enlazados por una transacción deben conservarse semánticamente.  
  
-   **Aislamiento** Una transacción es una unidad de aislamiento, y cada una se produce de forma aislada e independiente de las demás transacciones simultáneas.  Una transacción nunca debe ver las fases intermedias de otra transacción.  
  
-   **Durabilidad** Una transacción es una unidad de recuperación.  Si una transacción tiene éxito, sus actualizaciones persisten, incluso si el sistema se bloquea o se apaga.  Si se produce un error en una transacción, el sistema permanece en el estado anterior a la confirmación de la transacción.  
  
 Puede admitir transacciones en OLE DB \(consulte [Admitir transacciones en OLE DB](../data/oledb/supporting-transactions-in-ole-db.md)\) o en ODBC \(consulte [Transacción &#91;ODBC&#93;](../data/odbc/transaction-odbc.md)\).  
  
 Una transacción distribuida es una transacción que actualiza datos distribuidos, es decir, datos en más de un sistema de equipos en red.  Si desea admitir transacciones en un sistema distribuido, debe utilizar Microsoft.NET Framework en vez de la compatibilidad con transacciones de OLE DB.  
  
## Vea también  
 [Programación del acceso a datos \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)