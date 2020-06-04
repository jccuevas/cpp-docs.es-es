---
title: Advertencia del compilador C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: 474bdfa6eb670f39a2876b0c1490e7254cf216e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164913"
---
# <a name="compiler-warning-c4956"></a>Advertencia del compilador C4956

> '*Type*': este tipo no se pudo comprobar

## <a name="remarks"></a>Observaciones

Esta advertencia se genera cuando se especifica [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) y el código contiene un tipo que no es comprobable. La opción del compilador **/clr: Safe** está en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

Para obtener más información, consulte [código puro y comprobableC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Esta advertencia se emite como un error y se puede deshabilitar con la pragma [warning](../../preprocessor/warning.md) o la opción del compilador [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4956:

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```
