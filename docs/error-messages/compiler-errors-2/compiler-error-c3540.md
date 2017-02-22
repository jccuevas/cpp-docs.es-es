---
title: "Error del compilador C3540 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3540"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3540"
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3540
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"tipo": sizeof no se puede aplicar a un tipo que contiene "auto"  
  
 El operador [sizeof](../../cpp/sizeof-operator.md) no se puede aplicar al tipo indicado porque contiene el especificador `auto`.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3540.  
  
```  
// C3540.cpp  
// Compile with /Zc:auto  
int main() {  
    auto x = 123;  
    sizeof(x);    // OK  
    sizeof(auto); // C3540  
    return 0;  
}  
```  
  
## Vea también  
 [auto \(Palabra clave\)](../../cpp/auto-keyword.md)   
 [\/Zc:auto \(Deducir tipo de variable\)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof \(Operador\)](../../cpp/sizeof-operator.md)