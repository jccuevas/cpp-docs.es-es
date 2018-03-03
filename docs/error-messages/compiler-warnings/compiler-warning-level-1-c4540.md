---
title: Compilador advertencia (nivel 1) C4540 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aaaef1edaa6af093ae03fe69231a9686e3d087a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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