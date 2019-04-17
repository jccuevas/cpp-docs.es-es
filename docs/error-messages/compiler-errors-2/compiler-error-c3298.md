---
title: Error del compilador C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: fe6913d402c6ce4df3551c159eb56a12590799cb
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773909"
---
# <a name="compiler-error-c3298"></a>Error del compilador C3298

'restricción_1': no se puede usar 'restricción_2' como restricción porque 'restricción_2' tiene la restricción de referencia y 'restricción_1' tiene la restricción de valor.

No se pueden especificar características que se excluyen mutuamente para una restricción. Por ejemplo, un parámetro de tipo genérico no se puede restringir a un tipo de valor y a un tipo de referencia.

Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

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