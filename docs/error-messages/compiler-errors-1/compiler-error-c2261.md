---
title: Error del compilador C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: f23c2a38f8e4d6781af73fb70a25cf4737e2c4e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758780"
---
# <a name="compiler-error-c2261"></a>Error del compilador C2261

' cadena ': la referencia de ensamblado no es válida y no se puede resolver

Un valor no era válido.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> se utiliza para especificar un ensamblado de confianza. Por ejemplo, si un archivo. dll desea especificar b. dll como ensamblado de confianza, debe especificar (en un archivo. dll): InternalsVisibleTo ("b"). A continuación, el tiempo de ejecución permite a b. dll tener acceso a todo en un archivo. dll (excepto los tipos privados).

Para obtener más información sobre la sintaxis correcta al especificar ensamblados de confianza, vea [ensamblados de confianza (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2261.

```cpp
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```
