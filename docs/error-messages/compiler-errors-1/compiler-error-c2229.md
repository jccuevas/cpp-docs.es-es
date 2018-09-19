---
title: Error del compilador C2229 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2229
dev_langs:
- C++
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b235b5fae84ba605ecec5419f9334ccfa0a4be6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035596"
---
# <a name="compiler-error-c2229"></a>Error del compilador C2229

el tipo 'identifier' tiene una matriz de tamaño cero no válida

Un miembro de un estructura o campo de bits contiene una matriz de tamaño cero que no es el último miembro.

Dado que puede tener una matriz de tamaño cero como el último miembro del struct, debe especificar su tamaño al asignar la estructura.

Si la matriz de tamaño cero no es el último miembro del struct, el compilador no puede calcular el desplazamiento para los campos restantes.

El ejemplo siguiente genera C2229:

```
// C2229.cpp
struct S {
   int a[0];  // C2229  zero-sized array
   int b[1];
};

struct S2 {
   int a;
   int b[0];
};

int main() {
   // allocate 7 elements for b field
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];
   s2->b[6] = 100;
}
```