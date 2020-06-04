---
title: Error del compilador C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: 148433f0d959985eb5a874f588f8cbf9d377e8b7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735962"
---
# <a name="compiler-error-c3299"></a>Error del compilador C3299

'member_function': no puede especificar restricciones; estas se heredan del método base

Al reemplazar una función miembro genérica, no puede especificar cláusulas de restricción (la repetición de las restricciones implica que las restricciones no se heredan).

Se heredarán las cláusulas de restricción en la función genérica que está reemplazando.

Para más información, consulte [Restricciones de parámetros de tipo genérico](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3299.

```cpp
// C3299.cpp
// compile with: /clr /c
public ref struct R {
   generic<class T>
   where T : R
   virtual void f();
};

public ref struct S : R {
   generic<class T>
   where T : R   // C3299
   virtual void f() override;
};
```
