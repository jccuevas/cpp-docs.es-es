---
title: Error del compilador C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: e32ffca067c3b25120301527e7a708d53001d541
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376255"
---
# <a name="compiler-error-c3136"></a>Error del compilador C3136

'interface': una interfaz COM solo puede heredar de otra interfaz COM; 'interface' no es una interfaz COM

Una interfaz a la que se aplicó un [interface (atributo)](../../windows/attributes/interface-attributes.md) hereda de una interfaz que no es una interfaz COM. En última instancia hereda una interfaz COM de `IUnknown`. Cualquier interfaz precedida por un atributo de la interfaz es una interfaz COM.

El ejemplo siguiente genera C3136:

```
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