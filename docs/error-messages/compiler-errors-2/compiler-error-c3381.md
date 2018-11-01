---
title: Error del compilador C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: ae416d68831d1964c89d938dfcddd364e521195c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440279"
---
# <a name="compiler-error-c3381"></a>Error del compilador C3381

'ensamblado' : los especificadores de acceso al ensamblado sólo están disponibles en el código compilado con la opción /clr

Tipos nativos son visibles fuera del ensamblado, pero solo se puede especificar acceso de ensamblado para tipos nativos en un **/CLR** compilación.

Para obtener más información, consulte [escriba visibilidad](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) y [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3381.

```
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```