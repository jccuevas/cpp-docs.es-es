---
title: Compilador advertencia (nivel 1) C4584 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4584
dev_langs:
- C++
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba427de26d07851c5bf2a2dd3f599c4cbe7afc5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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