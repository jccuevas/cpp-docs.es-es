---
title: "Error del compilador C3491 | Microsoft Docs"
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
  - "C3491"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3491"
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3491
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': una captura por valor no se puede modificar en una expresión lambda no mutable  
  
 Una expresión lambda no mutable no puede modificar el valor de una variable capturada por valor.  
  
### Para corregir este error  
  
-   Declare la expresión lambda con la palabra clave `mutable`, o  
  
-   Pase la variable por referencia a la lista de captura de la expresión lambda.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3491 porque el cuerpo de una expresión lambda no mutable modifica la variable de captura `m`:  
  
```  
// C3491a.cpp int main() { int m = 55; [m](int n) { m = n; }(99); // C3491 }  
```  
  
## Ejemplo  
 En el ejemplo siguiente se resuelve el error C3491 mediante la declaración de la expresión lambda con la palabra clave `mutable`:  
  
```  
// C3491b.cpp int main() { int m = 55; [m](int n) mutable { m = n; }(99); }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)