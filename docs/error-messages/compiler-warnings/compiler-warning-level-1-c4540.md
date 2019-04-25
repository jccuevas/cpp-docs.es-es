---
title: Advertencia del compilador (nivel 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 86f6cd866f7708277ebba436ba7c076086dc9c8c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160710"
---
# <a name="compiler-warning-level-1-c4540"></a>Advertencia del compilador (nivel 1) C4540

dynamic_cast se ha utilizado para convertir a base inaccesible o ambigua; se producirá un error de prueba de tiempo de ejecución ('tipo1' a 'tipo2')

Se utiliza `dynamic_cast` para convertir de un tipo a otro. El compilador determina que la conversión siempre produciría un error (devolver **NULL**) porque una clase base es inaccesible (`private`, por ejemplo) o ambigua (aparece más de una vez en la jerarquía de clases, por ejemplo).

A continuación muestra un ejemplo de esta advertencia. Clase **B** se deriva de la clase **A**. El programa usa `dynamic_cast` para realizar la conversión de clase **B** (la clase derivada) a la clase **A**, siempre que se producirá un error porque clase **B** es `private` y, por tanto, no es accesible. Cambiar el acceso de **A** a **pública** resolverá la advertencia.

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