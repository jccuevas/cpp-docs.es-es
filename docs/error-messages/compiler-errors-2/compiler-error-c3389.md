---
title: Error del compilador C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: b166096390169939f01bcb976a57612f10f7df2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201141"
---
# <a name="compiler-error-c3389"></a>Error del compilador C3389

> __declspec (*palabra clave*) no se puede usar con/CLR: Pure o/CLR: Safe

## <a name="remarks"></a>Observaciones

Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

Un modificador de [__declspec](../../cpp/declspec.md) utilizado implica un estado por proceso.  [/clr: Pure](../../build/reference/clr-common-language-runtime-compilation.md) implica un estado por [AppDomain](../../cpp/appdomain.md) .  Por lo tanto, no se permite declarar una variable con el modificador de **__declspec** `keyword`y compilar con **/clr: Pure** .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
