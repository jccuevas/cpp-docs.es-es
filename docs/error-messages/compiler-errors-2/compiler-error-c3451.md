---
title: Error del compilador C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 2e0122dd53ba5318077dd33f22a07492c52db26b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756219"
---
# <a name="compiler-error-c3451"></a>Error del compilador C3451

' Attribute ': no se puede aplicar un atributo no administrado a ' type '

No C++ se puede aplicar un atributo a un tipo CLR. Consulte [ C++ referencia de atributos](../../windows/attributes/attributes-alphabetical-reference.md) para obtener más información.

Para obtener más información, consulta [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

Este error se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio 2005: el atributo [UUID](../../windows/uuid-cpp-attributes.md) ya no se permite en un atributo definido por el usuario mediante la programación de CLR. Utilice <xref:System.Runtime.InteropServices.GuidAttribute> en su lugar.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3451.

```cpp
// C3451.cpp
// compile with: /clr /c
using namespace System;
[ attribute(AttributeTargets::All) ]
public ref struct MyAttr {};

[ MyAttr, helpstring("test") ]   // C3451
// try the following line instead
// [ MyAttr ]
public ref struct ABC {};
```
