---
title: novtable | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: novtable_cpp
dev_langs: C++
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 26dc6677c6fcc7ab3834d3bb13d9e85dd0d8ede0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="novtable"></a>novtable
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Este es un atributo extendido `__declspec`.  
  
 Esta forma de `__declspec` se puede aplicar a cualquier declaración de clase, pero solo se debe aplicar a clases de interfaz puras, es decir, clases que nunca crearán instancias por sí solas. `__declspec` impide que el compilador genere código para inicializar vfptr en los constructores y el destructor de la clase. En muchos casos, esto quita las únicas referencias a la vtable asociadas a la clase y, en consecuencia, el vinculador la quita. El uso de esta forma de `__declspec` puede producir una reducción significativa del tamaño del código.  
  
 Si intenta crear una instancia de una clase marcada con `novtable` y, a continuación, tener acceso a un miembro de clase, recibirá una infracción de acceso (AV).  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
In Y  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)