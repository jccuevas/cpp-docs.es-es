---
title: Compilador advertencia (nivel 1) C4584 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4584
dev_langs:
- C++
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df3f92142fe42451ca7ae8272463d9347a263121
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4584"></a>Advertencia del compilador (nivel 1) C4584
'clase1': clase base 'clase2' ya es una clase base de 'Clase3'  
  
 La clase definida se hereda de dos clases: una de las cuales se hereda de otro. Por ejemplo:  
  
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
  
 En este caso, se emitirá una advertencia en la clase C, porque hereda de la clase A y clase B, que también hereda de la clase A. Esta advertencia sirve como recordatorio de que debe calificar totalmente el uso de los miembros de estas clases base o se generará un error del compilador debido a la ambigüedad en cuanto a qué miembro de clase se hace referencia.