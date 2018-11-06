---
title: Error del compilador C3296
ms.date: 11/04/2016
f1_keywords:
- C3296
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
ms.openlocfilehash: 2e9787b063a5a37af8d0e0fdd04492a743792646
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588115"
---
# <a name="compiler-error-c3296"></a>Error del compilador C3296

'propiedad': ya existe una propiedad con este nombre.

El compilador encontró más de una propiedad con el mismo nombre. Cada propiedad de un tipo debe tener un nombre único.

Para obtener más información, consulta [property](../../windows/property-cpp-component-extensions.md).

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