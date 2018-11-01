---
title: Error del compilador C3461
ms.date: 11/04/2016
f1_keywords:
- C3461
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
ms.openlocfilehash: 81372c7a2468becf6dba3b30b62ee266eed272ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562921"
---
# <a name="compiler-error-c3461"></a>Error del compilador C3461

'type': solamente se puede reenviar un tipo administrado

El reenvío de tipos solo puede realizarse con tipos CLR.  Consulte [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md) para obtener más información.

Para obtener más información, consulte [reenvío de tipos (C++ / c++ / CLI)](../../windows/type-forwarding-cpp-cli.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un componente.

```
// C3461.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3461.

```
// C3461b.cpp
// compile with: /clr /c
#using "C3461.dll"
class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3461
[assembly:TypeForwardedTo(R::typeid)];   // OK
```