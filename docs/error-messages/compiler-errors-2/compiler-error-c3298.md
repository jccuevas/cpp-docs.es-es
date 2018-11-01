---
title: Error del compilador C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: 8a2d8f6ab72a5e72a646cb1fca64635bc72dd2ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492852"
---
# <a name="compiler-error-c3298"></a>Error del compilador C3298

'restricción_1': no se puede usar 'restricción_2' como restricción porque 'restricción_2' tiene la restricción de referencia y 'restricción_1' tiene la restricción de valor.

No se pueden especificar características que se excluyen mutuamente para una restricción. Por ejemplo, un parámetro de tipo genérico no se puede restringir a un tipo de valor y a un tipo de referencia.

Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3298.

```
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```