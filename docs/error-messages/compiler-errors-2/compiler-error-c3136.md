---
title: Error del compilador C3136 | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 082a89b69092a8320f6bb4b930d01a7fd2de10c8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788388"
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