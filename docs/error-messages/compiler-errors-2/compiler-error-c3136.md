---
title: Error del compilador C3136 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 0439aa157a683065ccf7fff5b5f9d6d4d85e2f12
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054225"
---
# <a name="compiler-error-c3136"></a>Error del compilador C3136

'interface': una interfaz COM solo puede heredar de otra interfaz COM; 'interface' no es una interfaz COM

Una interfaz a la que se aplicó un [interface (atributo)](../../windows/interface-attributes.md) hereda de una interfaz que no es una interfaz COM. En última instancia hereda una interfaz COM de `IUnknown`. Cualquier interfaz precedida por un atributo de la interfaz es una interfaz COM.

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