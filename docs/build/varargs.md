---
title: "Varargs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Varargs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si los parámetros se pasan a través de varargs \(por ejemplo, argumentos de puntos suspensivos\), los parámetros se pasan normalmente incluyendo el quinto argumento y los siguientes.  También es responsabilidad del destinatario volcar los argumentos cuyas direcciones están tomadas.  Con valores de punto flotante, tanto el registro de enteros como de punto flotante contendrá el valor flotante en caso de que el destinatario espere el valor en el registro de enteros.  
  
## Vea también  
 [Convención de llamada](../build/calling-convention.md)