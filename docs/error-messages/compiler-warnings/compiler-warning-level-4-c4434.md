---
title: Advertencia del compilador (nivel 4) C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: 6a7d760a7d192c7e0a7bd5e16f77efe1a4099c31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591270"
---
# <a name="compiler-warning-level-4-c4434"></a>Advertencia del compilador (nivel 4) C4434

un constructor de clase debe tener accesibilidad privada; se cambiará a acceso privado

La advertencia C4434 indica que el compilador ha cambiado la accesibilidad de un constructor estático. Los constructores estáticos deben tener accesibilidad privada, ya que están concebidos para que sólo los llame Common Language Runtime. Para obtener más información, consulte [constructores estáticos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4434.

```
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```