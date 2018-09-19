---
title: Error irrecuperable C1191 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1191
dev_langs:
- C++
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: daefec7c89fc98d056963c4f761b7298d6e491cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062974"
---
# <a name="fatal-error-c1191"></a>Error irrecuperable C1191

solo se puede importar 'dll' en el ámbito global

La instrucción para importar mscorlib.dll en un programa que utiliza programación /clr no puede aparecer en un espacio de nombres o una función, pero debe aparecer en el ámbito global.

El ejemplo siguiente genera C1191:

```
// C1191.cpp
// compile with: /clr
namespace sample {
   #using <mscorlib.dll>   // C1191 not at global scope
}
```

Posible resolución:

```
// C1191b.cpp
// compile with: /clr /c
#using <mscorlib.dll>
namespace sample {}
```