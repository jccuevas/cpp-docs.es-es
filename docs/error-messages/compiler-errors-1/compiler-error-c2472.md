---
title: "Error del compilador C2472 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2472"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2472"
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2472
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' no se puede generar en código administrado: 'message'; compile con \/clr para generar una imagen mixta  
  
 Este error se producirá cuando se usen tipos no admitidos por código administrado en un entorno puro de Common Language Runtime \(CLR\). Compile con **\/clr** para resolver el error.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C2472.  
  
```  
// C2472.cpp // compile with: /clr:pure // C2472 expected #include <cstdlib> int main() { int * __ptr32 p32; int * __ptr64 p64; p32 = (int * __ptr32)malloc(4); p64 = p32; }  
```  
  
## Vea también  
 [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md)