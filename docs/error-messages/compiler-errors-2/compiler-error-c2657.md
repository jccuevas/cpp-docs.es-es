---
title: "Error del compilador C2657 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2657"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2657"
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2657
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase::\*' se ha encontrado al principio de una instrucción \(¿ha olvidado especificar un tipo?\)  
  
 La línea comenzaba con un identificador de puntero a miembro.  
  
 Este error puede ser debido a la falta de un especificador de tipo en la declaración de un puntero a un miembro.  
  
 El código siguiente genera el error C2657:  
  
```  
// C2657.cpp  
class C {};  
int main() {  
   C::* pmc1;        // C2657  
   int C::* pmc2;   // OK  
}  
```