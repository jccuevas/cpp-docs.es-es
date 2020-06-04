---
title: Advertencia del compilador (nivel 4) C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: fccc37ec531768adbe332ddf9fd91ceb708c7185
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990812"
---
# <a name="compiler-warning-level-4-c4434"></a>Advertencia del compilador (nivel 4) C4434

un constructor de clase debe tener accesibilidad privada; se cambiará a acceso privado

La advertencia C4434 indica que el compilador ha cambiado la accesibilidad de un constructor estático. Los constructores estáticos deben tener accesibilidad privada, ya que están concebidos para que sólo los llame Common Language Runtime. Para obtener más información, vea [constructores estáticos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4434.

```cpp
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```
