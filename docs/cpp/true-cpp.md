---
title: "true (C++) | Microsoft Docs"
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
  - "true_cpp"
  - "true"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "true (palabra clave) [C++]"
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# true (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
        bool-identifier = true ;  
bool-expression logical-operator true ;  
```  
  
## Comentarios  
 Esta palabra clave es uno de los dos valores para una variable de tipo [bool](../cpp/bool-cpp.md) o una expresión condicional \(una expresión condicional es ahora una expresión booleana true\).  Si `i` es de tipo `bool`, la instrucción `i = true;` asigna **true** a `i`.  
  
## Ejemplo  
  
```  
// bool_true.cpp  
#include <stdio.h>  
int main()  
{  
    bool bb = true;  
    printf_s("%d\n", bb);  
    bb = false;  
    printf_s("%d\n", bb);  
}  
```  
  
  **1**  
**0**   
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)