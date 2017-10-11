---
title: Error del compilador C2555 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 64f66bf80e8e4b6ba7477691cb9675cec347807d
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2555"></a>Error del compilador C2555
'clase1:: función1': función virtual de reemplazo tipo devuelto es diferente y no es covariante de 'clase2:: función2'  
  
 Una función virtual y una función reemplaza derivada tienen listas de parámetros idénticas pero diferentes tipos de valor devueltos. Una función de reemplazo en una clase derivada no puede diferir de una función virtual en una clase base solo por su tipo de valor devuelto.  
  
 Para resolver este error, convierta el valor devuelto después de llamar a la función virtual.  
  
 También puede ver este error si se compila con/CLR.   Por ejemplo, el equivalente en Visual C++ a la siguiente declaración de C#:  
  
```  
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);  
```  
  
 is  
  
```  
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];  
```  
  
 Para obtener más información sobre el error C2555, vea el artículo de Knowledge Base Q240862.  
  
 El ejemplo siguiente genera el error C2555:  
  
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
