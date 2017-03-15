---
title: "Error del compilador C3382 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3382"
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# Error del compilador C3382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'sizeof' no se admite con \/clr:safe  
  
 El archivo de resultados de una compilación **\/clr:safe** es un archivo de seguridad de tipos comprobable y el operador sizeof no se admite porque el valor devuelto del operador sizeof es size\_t, cuyo tamaño varía según el sistema operativo.  
  
 Para obtener más información, vea  
  
-   [sizeof \(Operador\)](../../cpp/sizeof-operator.md)  
  
-   [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Problemas comunes de migración a 64 bits en Visual C\+\+](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3382:  
  
```  
// C3382.cpp // compile with: /clr:safe int main() { sizeof( char );   // C3382 }  
```