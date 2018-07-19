---
title: Compilador advertencia (nivel 1) C4540 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3939ad2bbcba1ab3b492d83bdbb8f7076c2c5f2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283067"
---
# <a name="compiler-warning-level-1-c4540"></a>Advertencia del compilador (nivel 1) C4540
dynamic_cast se ha utilizado para convertir a base inaccesible o ambigua; se producirá un error de prueba en tiempo de ejecución ('tipo1' a 'tipo2')  
  
 Se utiliza `dynamic_cast` para convertir de un tipo a otro. El compilador determinó que la conversión siempre produciría un error (devolver **NULL**) porque una clase base es inaccesible (`private`, por ejemplo) o ambigua (aparece más de una vez en la jerarquía de clases, por ejemplo).  
  
 A continuación muestra un ejemplo de esta advertencia. Clase **B** se deriva de la clase **A**. El programa usa `dynamic_cast` para realizar la conversión de la clase **B** (la clase derivada) a clase **A**, siempre que se producirá un error porque clase **B** es `private` y, por tanto, no es accesible. Cambiar el acceso de **A** a **público** resolverá la advertencia.  
  
```  
// C4540.cpp  
// compile with: /W1  
  
struct A {   
   virtual void g() {}  
};  
  
struct B : private A {  
   virtual void g() {}  
};  
  
int main() {  
   B b;  
   A * ap = dynamic_cast<A*>(&b);   // C4540  
}  
```