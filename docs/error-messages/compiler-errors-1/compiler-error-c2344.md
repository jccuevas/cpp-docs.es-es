---
title: Error del compilador C2344
ms.date: 11/04/2016
f1_keywords:
- C2344
helpviewer_keywords:
- C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
ms.openlocfilehash: d1ba3a0f975dbc96c9c6ca51a8dac89b5a614572
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188177"
---
# <a name="compiler-error-c2344"></a>Error del compilador C2344

align(#): la alineación debe ser potencia de dos

Cuando se usa la palabra clave [align](../../cpp/align-cpp.md) , el valor pasado debe ser una potencia de dos.

Por ejemplo, el código siguiente genera el error C2344 porque 3 no es una potencia de dos:

```
// C2344.cpp
// compile with: /c
__declspec(align(3)) int a;   // C2344
__declspec(align(4)) int b;   // OK
```