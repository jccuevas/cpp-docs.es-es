---
title: Error del compilador C2959
ms.date: 11/04/2016
f1_keywords:
- C2959
helpviewer_keywords:
- C2959
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
ms.openlocfilehash: c45466fdf8d0c4bec67779943a5868299f05cf79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535738"
---
# <a name="compiler-error-c2959"></a>Error del compilador C2959

una función o clase genérica no puede ser un miembro de una plantilla

Para obtener más información, consulte [en tiempo de ejecución de Windows y plantillas administradas](../../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md) y [genéricos](../../windows/generics-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2959.

```
// C2959.cpp
// compile with: /clr /c
template <class T> ref struct S {
   generic <class U> ref struct GR1;   // C2959
};
```