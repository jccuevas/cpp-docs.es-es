---
title: Error del compilador C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: 436fb112758dfdec9997ff7e6dd7ef8f9dcdc66e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761782"
---
# <a name="compiler-error-c3163"></a>Error del compilador C3163

' Construct ': atributos incoherentes con la declaración anterior

Los atributos que se aplican a una definición entran en conflicto con los atributos que se aplican a una declaración.

Una manera de resolver C3163 es eliminar atributos en la declaración adelantada. Cualquier atributo de una declaración adelantada debe ser inferior a los atributos de la definición o, como máximo, iguales a ellos.

Una posible causa del error C3163 implica el lenguaje de anotación de código fuente (SAL) de Microsoft. Las macros SAL no se expanden a menos que compile el proyecto mediante el uso de la marca **/Analyze** . Un programa que se compila correctamente sin/Analyze podría iniciar C3163 si intenta volver a compilarlo con la opción/Analyze. Para obtener más información sobre SAL, consulte [anotaciones de sal](../../c-runtime-library/sal-annotations.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3163.

```cpp
// C3163.cpp
// compile with: /clr /c
using namespace System;

[CLSCompliant(true)] void f();
[CLSCompliant(false)] void f() {}   // C3163
// try the following line instead
// [CLSCompliant(true)] void f() {}
```

## <a name="see-also"></a>Vea también

[Anotaciones SAL](../../c-runtime-library/sal-annotations.md)
