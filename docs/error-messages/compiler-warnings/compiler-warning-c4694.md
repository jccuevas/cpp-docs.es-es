---
title: Advertencia del compilador C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: 6164fd2e19e35233ba67feb84d117f1e4e01f20d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778844"
---
# <a name="compiler-warning-c4694"></a>Advertencia del compilador C4694

> '*clase*': una clase abstracta sellada no puede tener una clase base *$base_class*'

Una clase abstracta y sellada no puede heredar de un tipo de referencia. Una clase sellada y abstracta no puede implementar las funciones de clase base ni permitir que se use como clase base.

Para obtener más información, consulte [abstracta](../../extensions/abstract-cpp-component-extensions.md), [sealed](../../extensions/sealed-cpp-component-extensions.md), y [clases y Structs](../../extensions/classes-and-structs-cpp-component-extensions.md).

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [advertencia #pragma](../../preprocessor/warning.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```