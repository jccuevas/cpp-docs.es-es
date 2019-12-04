---
title: Error del compilador C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: 75862f3b80d617b607a7b3e735cb3e16e9a40bb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757389"
---
# <a name="compiler-error-c3136"></a>Error del compilador C3136

' interfaz ': una interfaz COM solo puede heredar de otra interfaz COM, ' interfaz ' no es una interfaz COM

Una interfaz a la que se ha aplicado un [atributo de interfaz](../../windows/attributes/interface-attributes.md) hereda de una interfaz que no es una interfaz com. Una interfaz COM hereda en última instancia de `IUnknown`. Cualquier interfaz precedida por un atributo de interfaz es una interfaz COM.

En el ejemplo siguiente se genera C3136:

```cpp
// C3136.cpp
#include "unknwn.h"

__interface A   // C3136
// try the following line instead
// _interface A : IUnknown
{
   int a();
};

[object]
__interface B : A
{
   int aa();
};
```
