---
title: "Error del compilador C3541 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3541"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3541"
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3541
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"tipo": typeid no se puede aplicar a un tipo que contiene "auto"  
  
 El operador [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) no se puede aplicar al tipo indicado porque contiene el especificador `auto`.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3541.  
  
```  
// C3541.cpp  
// Compile with /Zc:auto  
#include <typeinfo>  
int main() {  
    auto x = 123;  
    typeid(x);    // OK  
    typeid(auto); // C3541  
    return 0;  
}  
```  
  
## Vea también  
 [auto \(Palabra clave\)](../../cpp/auto-keyword.md)   
 [\/Zc:auto \(Deducir tipo de variable\)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md)