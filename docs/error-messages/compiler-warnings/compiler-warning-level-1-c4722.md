---
title: Advertencia del compilador (nivel 1) C4722
ms.date: 11/04/2016
f1_keywords:
- C4722
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
ms.openlocfilehash: 320061c2daf2be042afe45828af637638399beaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327293"
---
# <a name="compiler-warning-level-1-c4722"></a>Advertencia del compilador (nivel 1) C4722

'function': el destructor nunca devuelve un valor, posible pérdida de memoria

El flujo de control finaliza en un destructor. Se cerrará el subproceso o el programa completo y no se pueden liberar recursos asignados.  Además, si se llama un destructor para desenredar la pila durante el procesamiento de la excepción, el comportamiento del ejecutable es indefinido.

Para resolver el problema, quite la llamada de función que hace que el destructor no devuelva ningún valor.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4722:

```
// C4722.cpp
// compile with: /O1 /W1 /c
#include <stdlib.h>
class C {
public:
   C();
   ~C() { exit(1); };   // C4722
};

extern void func (C*);

void Test(){
   C x;
   func(&x);
   // control will not leave Test because destructor will exit
}
```