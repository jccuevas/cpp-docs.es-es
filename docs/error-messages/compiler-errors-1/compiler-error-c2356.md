---
title: Error del compilador C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: e306c5a8f9175bc3c7902b20263aa2e451944182
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759937"
---
# <a name="compiler-error-c2356"></a>Error del compilador C2356

el segmento de inicialización no debe cambiar durante la unidad de traducción

Posibles causas:

- `#pragma init_seg` precedida por el código de inicialización de segmento

- `#pragma init_seg` precedida por otro `#pragma init_seg`

Para resolverlo, mueva el código de inicialización del segmento al principio del módulo. Si se deben inicializar varias áreas, muévalas a módulos independientes.

En el ejemplo siguiente se genera C2356:

```cpp
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```
