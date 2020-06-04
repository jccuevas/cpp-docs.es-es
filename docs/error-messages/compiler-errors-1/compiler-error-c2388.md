---
title: Error del compilador C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 21658a659468a6e2a0d911af70eefdaed320446c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745062"
---
# <a name="compiler-error-c2388"></a>Error del compilador C2388

' Symbol ': un símbolo no se puede declarar con __declspec (AppDomain) y \__declspec (proceso)

Los modificadores `appdomain` y `process` `__declspec` no pueden usarse en el mismo símbolo. El almacenamiento que existe para una variable es por proceso o por dominio de aplicación.

Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).

El ejemplo siguiente genera la advertencia C2388:

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
