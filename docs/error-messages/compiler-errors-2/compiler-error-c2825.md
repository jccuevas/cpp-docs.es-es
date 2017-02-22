---
title: "Error del compilador C2825 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2825"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2825"
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2825
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

var: debe ser una clase o espacio de nombres cuando vaya seguido de '::'  
  
 Se intentó formar un nombre completo, pero sin éxito.  
  
 Por ejemplo, asegúrese de que el código no contiene una declaración de función donde el nombre de función comienza con ::.  
  
## Ejemplo  
 El código siguiente genera el error C2825:  
  
```  
// C2825.cpp  
typedef int i;  
int main() {  
   int* p = new int;  
   p->i::i();   // C2825  
   // try the following line instead  
   // p->i::~i();  
}  
```