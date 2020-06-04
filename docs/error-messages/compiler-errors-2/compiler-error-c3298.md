---
title: Error del compilador C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: d5e9586b026e0092491c80c23f55080354c9e465
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760080"
---
# <a name="compiler-error-c3298"></a>Error del compilador C3298

'restricción_1': no se puede usar 'restricción_2' como restricción porque 'restricción_2' tiene la restricción de referencia y 'restricción_1' tiene la restricción de valor.

No se pueden especificar características que se excluyen mutuamente para una restricción. Por ejemplo, un parámetro de tipo genérico no se puede restringir a un tipo de valor y a un tipo de referencia.

Para más información, consulte [Restricciones de parámetros de tipo genérico](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3298.

```cpp
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```
