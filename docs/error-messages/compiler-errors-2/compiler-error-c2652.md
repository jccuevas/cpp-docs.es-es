---
title: "Error del compilador C2652 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2652"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2652"
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2652
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : constructor de copias no válido: el primer parámetro no debe ser un 'identificador'  
  
 El primer parámetro del constructor de copias tiene el mismo tipo que la clase, estructura o unión para la cual se definió.  El primer parámetro puede ser una referencia al tipo, pero no el propio tipo.  
  
 El código siguiente genera el error C2651:  
  
```  
// C2652.cpp  
// compile with: /c  
class A {  
   A( A );   // C2652 takes an A  
};  
class B {  
   B( B& );   // OK, reference to B  
};  
```