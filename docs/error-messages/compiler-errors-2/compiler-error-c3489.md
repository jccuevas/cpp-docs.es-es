---
title: "Error del compilador C3489 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3489"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3489"
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3489
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se necesita 'var' cuando el modo de captura predeterminado es por valor.  
  
 Cuando se especifica que el modo de captura predeterminado de una expresión lambda es por valor, no se puede pasar una variable por valor a la cláusula de captura de dicha expresión.  
  
### Para corregir este error  
  
-   No pase explícitamente la variable a la cláusula de captura.  
  
-   No especifique por valor como el modo de captura predeterminado.  
  
-   Especifique por referencia como el modo de captura predeterminado.  
  
-   Pase la variable por referencia a la cláusula de captura. \(Esto podría cambiar el comportamiento de la expresión lambda\).  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3489 porque la variable `n` por valor aparece en la cláusula de captura de una expresión lambda cuyo modo predeterminado es por valor:  
  
```  
// C3489a.cpp int main() { int n = 5; [=, n]() { return n; } (); // C3489 }  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestran cuatro posibles soluciones para C3489:  
  
```  
// C3489b.cpp int main() { int n = 5; // Possible resolution 1: // Do not explicitly pass n to the capture clause. [=]() { return n; } (); // Possible resolution 2: // Do not specify by-value as the default capture mode. [n]() { return n; } (); // Possible resolution 3: // Specify by-reference as the default capture mode. [&, n]() { return n; } (); // Possible resolution 4: // Pass n by reference to the capture clause. [&n]() { return n; } (); }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)