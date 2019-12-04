---
title: Error del compilador C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: eadc9b45b4cd4f2d9b533f387dadd66be8acc963
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749573"
---
# <a name="compiler-error-c3381"></a>Error del compilador C3381

'ensamblado' : los especificadores de acceso al ensamblado sólo están disponibles en el código compilado con la opción /clr

Los tipos nativos pueden ser visibles fuera del ensamblado, pero solo puede especificar el acceso de ensamblado para los tipos nativos en una compilación **/CLR** .

Para obtener más información, vea [visibilidad de tipos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) y [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3381.

```cpp
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```
