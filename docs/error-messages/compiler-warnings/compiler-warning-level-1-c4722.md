---
title: "Advertencia del compilador (nivel 1) C4722 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4722"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4722"
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4722
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': el destructor nunca devuelve un valor, posible pérdida de memoria  
  
 El flujo de control finaliza en un destructor. Se cerrará el subproceso o el programa completo y no se pueden liberar recursos asignados.  Además, si se llama un destructor para desenredar la pila durante el procesamiento de la excepción, el comportamiento del ejecutable es indefinido.  
  
 Para resolver el problema, quite la llamada de función que hace que el destructor no devuelva ningún valor.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4722:  
  
```  
// C4722.cpp // compile with: /O1 /W1 /c #include <stdlib.h> class C { public: C(); ~C() { exit(1); };   // C4722 }; extern void func (C*); void Test(){ C x; func(&x); // control will not leave Test because destructor will exit }  
```