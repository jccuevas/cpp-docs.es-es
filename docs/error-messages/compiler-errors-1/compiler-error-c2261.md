---
title: Error del compilador C2261 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2261
dev_langs:
- C++
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed43dc43fb6ceaf514a8e7452b06eb7bdaf7362
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051651"
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