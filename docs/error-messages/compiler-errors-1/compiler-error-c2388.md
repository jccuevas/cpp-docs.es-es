---
title: Error del compilador C2388 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2388
dev_langs:
- C++
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b6bcec4f5f218a52981a7770f5fa6e600494d9a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114155"
---
# <a name="compiler-error-c2388"></a>Error del compilador C2388

'símbolo': un símbolo no se puede declarar con ambos __declspec y \__declspec(process)

Los modificadores `appdomain` y `process` `__declspec` no pueden usarse en el mismo símbolo. El almacenamiento que existe para una variable es por proceso o por dominio de aplicación.

Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).

El ejemplo siguiente genera la advertencia C2388:

```
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```