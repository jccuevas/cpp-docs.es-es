---
title: Error del compilador C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: d1b7e1a69035df358cf84ad791f611928dab8b5a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773637"
---
# <a name="compiler-error-c3384"></a>Error del compilador C3384

'type_parameter': las restricciones de valor y de referencia son mutuamente exclusivas

No se puede restringir un tipo genérico tanto a `value class` como a `ref class`.

Consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3384.

```
// C3384.cpp
// compile with: /c /clr
generic <typename T>
where T : ref class
where T : value class   // C3384
ref class List {};
```