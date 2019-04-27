---
title: Error del compilador C2506
ms.date: 11/04/2016
f1_keywords:
- C2506
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
ms.openlocfilehash: 02f0a81204c4bc1c41111d32bae1c6946dee09ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164870"
---
# <a name="compiler-error-c2506"></a>Error del compilador C2506

'member': '__declspec (modificador)' no se puede aplicar a este símbolo

No puede declarar miembros estáticos de una clase administrada por proceso o por appdomain.

Vea [appdomain](../../cpp/appdomain.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2506.

```
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```