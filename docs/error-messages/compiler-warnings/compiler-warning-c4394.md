---
title: Advertencia del compilador C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: f74c115a3cabb421ba5a9cf4c34696a0c223512e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165280"
---
# <a name="compiler-warning-c4394"></a>Advertencia del compilador C4394

'función': el símbolo por AppDomain no se debe marcar con __declspec(dllexport)

Una función marcada con el modificador de [appdomain](../../cpp/appdomain.md)`__declspec` se COMPILA en MSIL (no en nativo) y las tablas de exportación (modificador de`__declspec` de[exportación](../../windows/export.md) ) no son compatibles con las funciones administradas.

Puede declarar una función administrada para tener accesibilidad pública. Para obtener más información, vea [visibilidad de tipos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) y visibilidad de [miembros](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).

La advertencia C4394 siempre se emite como error.  Puede desactivar esta advertencia con el `#pragma warning` o **/WD**; vea [Warning](../../preprocessor/warning.md) o [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/wo,/WV,/WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md) para obtener más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4394.

```cpp
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```
