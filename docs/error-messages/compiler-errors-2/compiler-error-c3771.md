---
title: "Error del compilador C3771 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3771"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3771"
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error del compilador C3771
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"identifier": no se puede encontrar ninguna declaración friend en el ámbito del espacio de nombres más próximo  
  
 La declaración de la plantilla de clase de la plantilla especificada *identifier* no se encuentra en el espacio de nombres actual.  
  
### Para corregir este error  
  
-   Asegúrese de que la declaración de la plantilla de clase del identificador de plantilla está definida en el espacio de nombres actual o que el identificador de plantilla sea un nombre completo.  
  
## Ejemplo  
 En el ejemplo de código siguiente se declara una función y plantilla de clase en el espacio de nombres `NA`, pero se intenta declarar una plantilla de función friend en el espacio de nombres `NB`.  
  
```  
// C3771.cpp // compile with: /c namespace NA { template<class T> class A { void aFunction(T t) {}; }; } // using namespace NA; namespace NB { class X { template<class T> friend void A<T>::aFunction(T); // C3771 // try the following line instead //      template<class T> friend void NA::A<T>::aFunction(T); // or try "using namespace NA;" instead. }; }  
```  
  
## Vea también  
 [Especificaciones de plantilla](../Topic/Template%20Specifications.md)