---
title: "noinline | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "noinline"
  - "noinline_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], noinline"
  - "noinline __declspec (palabra clave)"
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# noinline
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 **\_\_declspec\(noinline\)** indica al compilador que nunca alinee una función miembro determinada \(una función de una clase\).  
  
 Puede merecer la pena no alinear una función si es pequeña y no es crítica para el rendimiento del código.  Es decir, si la función es pequeña y no se la llamará a menudo, por ejemplo, una función que controla una condición de error.  
  
 Tenga en cuenta que si una función se marca como `noinline`, la función de llamada será más pequeña y, por tanto, será por sí misma un candidato para la alineación del compilador.  
  
```  
class X {  
   __declspec(noinline) int mbrfunc() {  
      return 0;   
   }   // will not inline  
};  
```  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [inline, \_\_inline, \_\_forceinline](../misc/inline-inline-forceinline.md)