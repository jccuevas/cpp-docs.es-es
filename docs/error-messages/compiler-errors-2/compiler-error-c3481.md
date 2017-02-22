---
title: "Error del compilador C3481 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3481"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3481"
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3481
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': no se encuentra la variable de captura lambda  
  
 El compilador no puede encontrar la definición de una variable que se pasó a la lista de capturas de una expresión lambda.  
  
### Para corregir este error  
  
-   Quite la variable de la lista de capturas de la expresión lambda.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3481 porque la variable `n` no está definida:  
  
```  
// C3481.cpp int main() { [n] {}(); // C3481 }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)