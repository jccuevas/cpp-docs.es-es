---
title: Error del compilador C3451 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3451
dev_langs:
- C++
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8685b75684827b4f202317e1df72a8248f1b41dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085204"
---
# <a name="compiler-error-c3451"></a>Error del compilador C3451

'attribute': no se puede aplicar el atributo no administrado a 'type'

No se puede aplicar un atributo de C++ a un tipo CLR. Consulte [referencia de atributos de C++](../../windows/cpp-attributes-reference.md) para obtener más información.

Para obtener más información, consulte [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).

Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: el [uuid](../../windows/uuid-cpp-attributes.md) atributo ya no se permite en un atributo definido por el usuario mediante programación con CLR. Utilice <xref:System.Runtime.InteropServices.GuidAttribute> en su lugar.

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