---
title: "Admitir transacciones en OLE DB | Microsoft Docs"
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
  - "transacciones distribuidas [C++]"
  - "transacciones anidadas [C++]"
  - "OLE DB [C++], compatibilidad con transacciones"
  - "plantillas de consumidor OLE DB [C++], compatibilidad con transacciones"
  - "transacciones [C++], compatibilidad de OLE DB"
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Admitir transacciones en OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una [transacción](../../data/transactions-mfc-data-access.md) es una forma de agrupar, o de procesar por lotes, una serie de actualizaciones que se van a realizar en un origen de datos, de forma que todas tengan éxito y se confirmen de una vez, o \(si se produce un error en una de ellas\) no se confirme ninguna y se revierta toda la transacción.  Este proceso garantiza la integridad del resultado en el origen de datos.  
  
 OLE DB admite transacciones con los tres métodos siguientes:  
  
-   [\<caps:sentence id\="tgt4" sentenceid\="0699a86bb6d6316bff035b804a56f0aa" class\="tgtSentence"\>ITransactionLocal::StartTransaction\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms709786.aspx)  
  
-   [\<caps:sentence id\="tgt5" sentenceid\="39299b0fea086b86052550bd165334f7" class\="tgtSentence"\>ITransaction::Commit\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms713008.aspx)  
  
-   [\<caps:sentence id\="tgt6" sentenceid\="8e992150c28ae247d532408ca7828bfe" class\="tgtSentence"\>ITransaction::Abort\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms709833.aspx)  
  
## Relación de sesiones y transacciones  
 Un único objeto de origen de datos puede crear uno o varios objetos de sesión, cada uno de los cuales puede hallarse dentro o fuera del ámbito de una transacción en un momento dado.  
  
 Cuando una sesión no entra en una transacción, todo el trabajo hecho en esa sesión en el almacén de datos queda confirmado inmediatamente en cada llamada de método. A veces se denomina modo de confirmación automática o modo implícito.  
  
 Cuando una sesión entra en una transacción, todo el trabajo realizado en esa sesión en el almacén de datos forma parte de la transacción y se confirma o anula como una unidad. A veces se denomina modo de confirmación manual.  
  
 La compatibilidad con transacciones es específica de cada proveedor.  Si el proveedor que utiliza admite el uso de transacciones, un objeto de sesión que admita **ITransaction** e **ITransactionLocal** puede participar en una transacción simple \(no anidada\).  La clase [CSession](../../data/oledb/csession-class.md) de las plantillas OLE DB admite estas interfaces y es la forma recomendada para implementar la compatibilidad con transacciones en Visual C\+\+.  
  
## Iniciar y finalizar la transacción  
 Se llama a los métodos `StartTransaction`, **Commit** y **Abort** en el objeto de conjunto de filas del consumidor.  
  
 Al llamar a **ITransactionLocal::StartTransaction** se inicia una nueva transacción local.  Una vez iniciada, los cambios forzados por sucesivas operaciones no se aplican realmente al almacén de datos hasta que se confirme la transacción.  
  
 Al llamar a **ITransaction::Commit** o **ITransaction::Abort** se finaliza la transacción.  **Commit** hace que todos los cambios incluidos en el ámbito de la transacción se apliquen al almacén de datos.  **Abort** hace que se cancelen todos los cambios dentro del ámbito de la transacción y el almacén de datos quede en el estado que tenía antes de comenzar la transacción.  
  
## Transacciones anidadas  
 Una [transacción anidada](https://msdn.microsoft.com/en-us/library/ms716985.aspx) se produce al iniciar una nueva transacción local cuando ya existe una transacción activa en la sesión.  La nueva transacción se inicia como una transacción anidada bajo la transacción actual.  Si el proveedor no admite transacciones anidadas, al llamar a `StartTransaction` cuando ya hay una transacción activa en la sesión, se devuelve **XACT\_E\_XTIONEXISTS**.  
  
## Transacciones distribuidas  
 Una transacción distribuida es una transacción que actualiza datos distribuidos; es decir, datos repartidos en más de un equipo de una red.  Si se desea admitir transacciones en un sistema distribuido, se debe utilizar .NET Framework en lugar de la compatibilidad con transacciones de OLE DB.  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)