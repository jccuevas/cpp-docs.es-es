---
title: Error del compilador C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 07cfda76af26ddb285be4f77131aaf48a20a761f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447853"
---
# <a name="compiler-error-c3451"></a>Error del compilador C3451

'attribute': no se puede aplicar el atributo no administrado a 'type'

No se puede aplicar un atributo de C++ a un tipo CLR. Consulte [referencia de atributos de C++](../../windows/attributes/attributes-alphabetical-reference.md) para obtener más información.

Para obtener más información, consulte [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio 2005: el [uuid](../../windows/uuid-cpp-attributes.md) atributo ya no se permite en un atributo definido por el usuario mediante programación con CLR. Utilice <xref:System.Runtime.InteropServices.GuidAttribute> en su lugar.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3451.

```
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