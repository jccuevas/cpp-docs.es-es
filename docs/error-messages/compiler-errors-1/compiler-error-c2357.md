---
title: Error del compilador C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: 1872672e776ad13bf16be5ae69729f4f68d8f3b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531786"
---
# <a name="compiler-error-c2357"></a>Error del compilador C2357

'identifier': debe ser una función de tipo 'type'

El código declara una versión de la `atexit` función que no coincide con la versión declarada internamente por el compilador. Declarar `atexit` como sigue:

```
int __cdecl atexit(void (__cdecl *)());
```

Para obtener más información, consulte [init_seg](../../preprocessor/init-seg.md).

El ejemplo siguiente genera C2357:

```
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```