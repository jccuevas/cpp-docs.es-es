---
title: Del compilador (nivel 1) de la advertencia C4722 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4722
dev_langs:
- C++
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f450120ff05c7e13888bf4b4ce4425405525b4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112504"
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