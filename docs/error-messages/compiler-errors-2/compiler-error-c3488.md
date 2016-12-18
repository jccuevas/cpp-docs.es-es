---
title: "Error del compilador C3488 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3488"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3488"
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3488
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se permite el uso de 'var' cuando el modo de captura predeterminado es por referencia  
  
 Cuando se especifica que el modo de captura predeterminado de una expresión lambda es por referencia, no se puede pasar una variable por referencia a la cláusula capture de dicha expresión.  
  
### Para corregir este error  
  
-   No pase explícitamente la variable a la cláusula de captura.  
  
-   No especifique por referencia como el modo de captura predeterminado.  
  
-   Especifique por valor como el modo de captura predeterminado.  
  
-   Pase la variable por valor a la cláusula de captura. \(Esto podría cambiar el comportamiento de la expresión lambda\).  
  
## Ejemplo  
 El ejemplo siguiente genera el código C3488 porque una referencia a la variable `n` aparece en la cláusula de captura de una expresión lambda cuya modo predeterminado es por referencia:  
  
```  
// C3488a.cpp int main() { int n = 5; [&, &n]() { return n; } (); // C3488 }  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra cuatro las posibles resoluciones a C3488:  
  
```  
// C3488b.cpp int main() { int n = 5; // Possible resolution 1: // Do not explicitly pass &n to the capture clause. [&]() { return n; } (); // Possible resolution 2: // Do not specify by-reference as the default capture mode. [&n]() { return n; } (); // Possible resolution 3: // Specify by-value as the default capture mode. [=, &n]() { return n; } (); // Possible resolution 4: // Pass n by value to the capture clause. [n]() { return n; } (); }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)