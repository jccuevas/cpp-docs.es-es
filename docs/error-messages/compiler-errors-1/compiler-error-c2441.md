---
title: Error del compilador C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 4e5d5335717ec77c61069ad08e209f9e1851dc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205314"
---
# <a name="compiler-error-c2441"></a>Error del compilador C2441

> '*variable*': un símbolo declarado con __declspec (proceso) debe ser const en el modo/CLR: Pure

## <a name="remarks"></a>Observaciones

Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

De forma predeterminada, las variables son por dominio de aplicación en **/clr: Pure**. Una variable marcada como `__declspec(process)` en **/clr: Pure** es propensa a errores si se modifica en un dominio de aplicación y se lee en otro.

Por consiguiente, el compilador exige que las variables por proceso se `const` en **/clr: Pure**, lo que hace que sean de solo lectura en todos los dominios de aplicación.

Para obtener más información, vea [Process](../../cpp/process.md) y [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2441.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```
