---
title: "Error del compilador C3495 | Microsoft Docs"
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
  - "C3495"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3495"
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3495
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': una captura lambda debe tener una duración de almacenamiento automática  
  
 No se puede capturar una variable que no tiene una duración de almacenamiento automática, como una variable que está marcada como `static` o `extern`.  
  
### Para corregir este error  
  
-   No pase una variable `static` o `extern` a la lista de captura de la expresión lambda.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3495 porque la variable de `static``n` aparece en la lista de captura de una expresión lambda:  
  
```  
// C3495.cpp int main() { static int n = 66; [&n]() { return n; }(); // C3495 }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)   
 [\(NO ESTÁ EN LA COMPILACIÓN\) Especificadores de clase de almacenamiento](http://msdn.microsoft.com/es-es/10b3d22d-cb40-450b-994b-08cf9a211b6c)