---
title: "novtable | Microsoft Docs"
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
  - "novtable"
  - "novtable_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], novtable"
  - "novtable __declspec (palabra clave)"
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# novtable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Este es un atributo extendido `__declspec`.  
  
 Esta forma de `__declspec` se puede aplicar a cualquier declaración de clase, pero solo se debe aplicar a clases de interfaz puras, es decir, clases que nunca crearán instancias por sí solas.  `__declspec` impide que el compilador genere código para inicializar vfptr en los constructores y el destructor de la clase.  En muchos casos, esto quita las únicas referencias a la vtable asociadas a la clase y, en consecuencia, el vinculador la quita.  El uso de esta forma de `__declspec` puede producir una reducción significativa del tamaño del código.  
  
 Si intenta crear una instancia de una clase marcada con `novtable` y, a continuación, tener acceso a un miembro de clase, recibirá una infracción de acceso \(AV\).  
  
## Ejemplo  
  
```  
// novtable.cpp  
#include <stdio.h>  
  
struct __declspec(novtable) X {  
   virtual void mf();  
};  
  
struct Y : public X {  
   void mf() {  
      printf_s("In Y\n");  
   }  
};  
  
int main() {  
   // X *pX = new X();  
   // pX->mf();   // Causes a runtime access violation.  
  
   Y *pY = new Y();  
   pY->mf();  
}  
```  
  
  **En Y**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)