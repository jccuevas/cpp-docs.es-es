---
title: "Error matem&#225;tico M6111 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6111"
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error matem&#225;tico M6111
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

subdesbordamiento de la pila  
  
 Una operación de punto flotante ha originado un subdesbordamiento de la pila en el coprocesador 8087\/287\/387 o en el emulador.  
  
 La causa de este error suele ser una llamada a una función `long double` que no devuelve un valor.  Este error se genera, por ejemplo, por la siguiente secuencia una vez compilada y ejecutada:  
  
```  
long double ld() {};  
main ()  
{  
  ld();  
}  
```  
  
 El programa termina con el código de salida 139.