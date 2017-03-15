---
title: "Advertencia del compilador (nivel 1) C4584 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4584"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4584"
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4584
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase1' : la clase base 'clase2' ya es una clase base de 'clase3'  
  
 La clase definida se deriva de dos clases, una de las cuales se deriva de la otra.  Por ejemplo:  
  
```  
// C4584.cpp  
// compile with: /W1 /LD  
class A {  
};  
  
class B : public A {  
};  
  
class C : public A, public B { // C4584  
};  
```  
  
 En este caso, se puede emitir una advertencia en la clase C, ya que hereda de la clase A y de la clase B que a su vez hereda de la A.  Esta advertencia sirve como aviso para recordar que hay que calificar completamente el uso de miembros de estas clases base; de lo contrario, se generará un error del compilador debido a la ambigüedad en los miembros de clase a los que se hace referencia.