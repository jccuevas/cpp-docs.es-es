---
title: Advertencia del compilador C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: daf5423588d08260239c3cff5a68532a358d07b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165124"
---
# <a name="compiler-warning-c4694"></a>Advertencia del compilador C4694

> '*Class*': una clase abstracta sellada no puede tener una clase base '*BASE_CLASS*'

Una clase abstracta y sellada no puede heredar de un tipo de referencia. Una clase sellada y abstracta no puede implementar las funciones de clase base ni permitir que se use como clase base.

Para obtener más información, vea [abstract](../../extensions/abstract-cpp-component-extensions.md), [Sealed](../../extensions/sealed-cpp-component-extensions.md), y [clases y Structs](../../extensions/classes-and-structs-cpp-component-extensions.md).

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [#pragma ADVERTENCIA](../../preprocessor/warning.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```
