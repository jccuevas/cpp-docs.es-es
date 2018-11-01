---
title: Error del compilador C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: 0166cce6011017b8a18821666083f7c47f58b7a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508119"
---
# <a name="compiler-error-c2356"></a>Error del compilador C2356

el segmento de inicialización no debe cambiar durante la unidad de traducción

Causas posibles:

- `#pragma init_seg` precedido por el código de inicialización de segmento

- `#pragma init_seg` precedido por otro `#pragma init_seg`

Para resolver, mueva el código de inicialización del segmento al principio del módulo. Si se deben inicializar varias áreas, muévalos a módulos separados.

El ejemplo siguiente genera C2356:

```
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```