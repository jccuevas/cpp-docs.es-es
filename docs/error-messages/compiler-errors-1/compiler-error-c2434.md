---
title: Error del compilador C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: 869db3b49075fa477860e045e59306e22a381ca4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205470"
---
# <a name="compiler-error-c2434"></a>Error del compilador C2434

> '*Symbol*': un símbolo declarado con __declspec (Process) no se puede inicializar dinámicamente en el modo/CLR: Pure

## <a name="remarks"></a>Observaciones

Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

No es posible inicializar dinámicamente una variable por proceso en **/clr: Pure**. Para obtener más información, vea [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) y [Process](../../cpp/process.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2434. Para corregir este problema, utilice constantes para inicializar `process` variables.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```
