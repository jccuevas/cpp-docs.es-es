---
title: "Error del compilador C3531 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3531"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3531"
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3531
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"símbolo": un símbolo cuyo tipo contiene "auto" debe tener un inicializador  
  
 La variable especificada no tiene una expresión de inicializador.  
  
### Para corregir este error  
  
1.  Especifique una expresión de inicializador, como una asignación simple que usa la sintaxis de signo igual, al declarar la variable.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3531 porque las variables `x1`, `y1, y2, y3` y `z2` no se inicializan.  
  
```  
// C3531.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto x1;                  // C3531  
   auto y1, y2, y3;          // C3531  
   auto z1 = 1, z2, z3 = -1; // C3531  
   return 0;  
}  
```  
  
## Vea también  
 [auto \(Palabra clave\)](../../cpp/auto-keyword.md)