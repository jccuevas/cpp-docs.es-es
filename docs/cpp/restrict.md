---
title: "restrict | Microsoft Docs"
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
  - "restrict"
  - "restrict_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], restrict"
  - "restrict __declspec (palabra clave)"
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# restrict
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Se aplica a una declaración de función o a una definición que devuelve un tipo de puntero e indica al compilador que la función devuelve un objeto que no tendrá alias de ningún otro puntero.  
  
## Sintaxis  
  
```  
__declspec(restrict) return_type f();  
```  
  
## Comentarios  
 El compilador propagará `__declspec(restrict)`.  Por ejemplo, la función `malloc` de CRT se decora con `__declspec(restrict)` y, por consiguiente, también se implica que los punteros inicializados en ubicaciones de memoria con `malloc` no tienen alias.  
  
 El compilador no comprueba que el puntero no tiene alias realmente.  Es responsabilidad del programador garantizar que el programa no utilice un alias de un puntero marcado con el modificador `restrict __declspec`.  
  
 Para conocer la semántica similar en las variables, vea [\_\_restrict](../cpp/extension-restrict.md).  
  
## Ejemplo  
 Vea [noalias](../cpp/noalias.md) para obtener un ejemplo con `restrict`.  
  
 Para obtener información sobre la palabra clave restrict que forma parte de C\+\+ AMP, vea [restrict \(C\+\+ AMP\)](../cpp/restrict-cpp-amp.md).  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)