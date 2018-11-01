---
title: Error del compilador C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: b5c689842f59a9cf999de08f10926efce0ade5ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490212"
---
# <a name="compiler-error-c3163"></a>Error del compilador C3163

'construcción': atributos incoherentes con la declaración anterior

Los atributos que se aplican a una definición de entrar en conflicto con los atributos que se aplican a una declaración.

Una manera de resolver C3163 es eliminar atributos en la declaración adelantada. Ningún atributo en una declaración adelantada debe ser menor que los atributos en la definición o, a lo sumo, igual a ellos.

Una posible causa del error C3163 implica el lenguaje de anotación de código de origen de Microsoft (SAL). Las macros SAL no expandirán a menos que compile el proyecto mediante el uso de la **/ analyze** marca. Un programa que se compila correctamente sin / analyze podría producir C3163 si se intenta volver a compilar con la / opción de análisis. Para obtener más información acerca de SAL, consulte [anotaciones SAL](../../c-runtime-library/sal-annotations.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3163.

```
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