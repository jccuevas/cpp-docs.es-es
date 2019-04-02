---
title: Error del compilador C3296
ms.date: 11/04/2016
f1_keywords:
- C3296
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
ms.openlocfilehash: c0a162590ac2a72dda17b2ecfc96899e94cde24c
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767046"
---
# <a name="compiler-error-c3296"></a>Error del compilador C3296

'propiedad': ya existe una propiedad con este nombre.

El compilador encontró más de una propiedad con el mismo nombre. Cada propiedad de un tipo debe tener un nombre único.

Para obtener más información, consulta [property](../../extensions/property-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3296.

```
// C3296.cpp
// compile with: /clr /c
using namespace System;

ref class R {
public:
   property int MyProp[int] { int get(int); }

   property String^ MyProp[int] { void set(int, String^); }   // C3296
};
```