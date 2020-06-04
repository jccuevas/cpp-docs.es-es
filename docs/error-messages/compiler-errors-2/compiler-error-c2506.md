---
title: Error del compilador C2506
ms.date: 11/04/2016
f1_keywords:
- C2506
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
ms.openlocfilehash: 593fbbc6b561e6390624aa79af14dc665a552990
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746843"
---
# <a name="compiler-error-c2506"></a>Error del compilador C2506

' Member ': ' __declspec (modificador) ' no se puede aplicar a este símbolo

No se puede declarar por proceso o por AppDomain para los miembros estáticos de una clase administrada.

Vea [appdomain](../../cpp/appdomain.md) para obtener más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2506.

```cpp
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```
