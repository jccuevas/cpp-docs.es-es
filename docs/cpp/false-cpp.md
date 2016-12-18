---
title: "false (C++) | Microsoft Docs"
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
  - "false_cpp"
  - "false"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "false (palabra clave) [C++]"
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# false (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave es uno de los dos valores para una variable de tipo [bool](../cpp/bool-cpp.md) o una expresión condicional \(una expresión condicional es ahora una expresión **true** Booleana\).  Por ejemplo, si `i` es una variable de tipo `bool`, la instrucción `i = false;` asigna **false** a `i`.  
  
## Ejemplo  
  
```  
// bool_false.cpp  
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