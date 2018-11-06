---
title: Error del compilador C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: 2df788efd93fb531822d858ea5aee1722487db81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535751"
---
# <a name="compiler-error-c2261"></a>Error del compilador C2261

'string': referencia de ensamblado no es válida y no se puede resolver

Un valor no era válido.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> se utiliza para especificar un ensamblado de confianza. Por ejemplo, si a.dll desea especificar b.dll como un ensamblado de confianza, podría especificar (en a.dll): InternalsVisibleTo("b"). El tiempo de ejecución, a continuación, permite b.dll tener acceso a todo el contenido de a.dll (excepto los tipos privados).

Para obtener más información sobre la sintaxis correcta al especificar los ensamblados de confianza, consulte [ensamblados Friend (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2261.

```
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```