---
title: Error del compilador C2250 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2250
dev_langs:
- C++
helpviewer_keywords:
- C2250
ms.assetid: f990986f-5c7d-4af4-a25c-b35540f1e217
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a50443932a2b8cb3ef6e66989ee53322de29868d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171577"
---
# <a name="compiler-error-c2250"></a>Error del compilador C2250
'identificador': herencia ambigua de 'clase:: miembro'  
  
 La clase derivada hereda más de un reemplazo de una función virtual de una clase base virtual. Estas invalidaciones son ambiguas en la clase derivada.  
  
 El ejemplo siguiente genera la advertencia C2286:  
  
```  
// C2250.cpp  
// compile with: /c  
// C2250 expected  
struct V {  
   virtual void vf();  
};  
  
struct A : virtual V {  
   void vf();  
};  
  
struct B : virtual V {  
   void vf();  
};  
  
struct D : A, B {  
   // Uncomment the following line to resolve.  
   // void vf();  
};  
```