---
title: "Error del compilador C2555 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2555"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2555"
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2555
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase1::función1': el tipo de valor devuelto de la función virtual de reemplazo es distinto y no es covariante de 'clase2::función2'  
  
 Una función virtual y una función de reemplazo derivada tienen listas de parámetros idénticas, pero tipos de valor devuelto diferentes.  Una función de reemplazo de una clase derivada no puede ser diferente de una función virtual en una clase base sólo por su tipo de valor devuelto.  
  
 Para resolver este problema, convierta el tipo de valor devuelto después de llamar a la función virtual.  
  
 También puede aparecer este error si compila con \/clr.   Por ejemplo, el equivalente de Visual C\+\+ para la siguiente declaración de C\#:  
  
```  
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);  
```  
  
 es  
  
```  
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];  
```  
  
 Para obtener más información sobre el error C2555, consulte el artículo Q240862 de Knowledge Base.  
  
 El código siguiente genera el error C2555:  
  
```  
// C2555.cpp  
// compile with: /c  
struct X {  
   virtual void func();  
};  
struct Y : X {  
   char func();  // C2555  
   void func2();   // OK  
};  
```