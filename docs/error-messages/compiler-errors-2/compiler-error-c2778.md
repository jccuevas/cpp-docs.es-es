---
title: Error del compilador C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 56c316ac971d0bdd1a0ca27ef8d4282acbe24779
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490518"
---
# <a name="compiler-error-c2778"></a>Error del compilador C2778

GUID formado incorrectamente en __declspec(uuid())

Se proporcionó un GUID incorrecto para el [uuid](../../cpp/uuid-cpp.md) atributo extendido.

El GUID debe ser una cadena de números hexadecimales con el formato siguiente:

```
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

El `uuid` atributo extendido acepta cadenas reconocidas por [CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring), con o sin delimitadores de llaves.

El ejemplo siguiente genera C2778:

```
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```