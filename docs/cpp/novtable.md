---
title: novtable | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- novtable
- novtable_cpp
dev_langs:
- C++
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 7064bd08a97f3eabbf337b1a351614e94d6458dd
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
