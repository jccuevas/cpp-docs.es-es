---
title: Advertencia del compilador C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: c125fa84119c62e3090611c9a841f46eee759711
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165215"
---
# <a name="compiler-warning-c4439"></a>Advertencia del compilador C4439

' función ': la definición de función con un tipo administrado en la signatura debe tener una Convención de llamada __clrcall

El compilador reemplaza implícitamente una Convención de llamada con [__clrcall](../../cpp/clrcall.md). Para resolver esta advertencia, quite la Convención de llamada `__cdecl` o `__stdcall`.

C4439 siempre se emite como un error. Puede desactivar esta advertencia con el `#pragma warning` o **/WD**; vea [Warning](../../preprocessor/warning.md) o [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/wo,/WV,/WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md) para obtener más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4439.

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```
