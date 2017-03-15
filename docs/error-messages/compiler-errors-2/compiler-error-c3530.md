---
title: "Error del compilador C3530 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3530"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3530"
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3530
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"auto" no se puede combinar con ningún otro especificador de tipo  
  
 Un especificador de tipo se usa con la palabra clave `auto`.  
  
### Para corregir este error  
  
1.  No use un especificador de tipo en una declaración de variable que usa la palabra clave `auto`.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3530 porque la variable `x` se declara tanto con la palabra clave `auto` como con el tipo `int` y porque el ejemplo se compila con **\/Zc:auto**.  
  
```  
// C3530.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto int x;   // C3530  
   return 0;  
}  
```  
  
## Vea también  
 [auto \(Palabra clave\)](../../cpp/auto-keyword.md)