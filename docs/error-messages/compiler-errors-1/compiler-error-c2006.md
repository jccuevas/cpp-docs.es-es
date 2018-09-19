---
title: Error del compilador C2006 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9468be17584a54047563bace2b35f5cb4888b41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031215"
---
# <a name="compiler-error-c2006"></a>Error del compilador C2006

'directiva' esperaba un nombre de archivo, que pero se encontró 'token'

Las directivas como [#include](../../preprocessor/hash-include-directive-c-cpp.md) o [#import](../../preprocessor/hash-import-directive-cpp.md) requieren un nombre de archivo. Para resolver el error, asegúrese de que *token* es un nombre de archivo válido. Además, coloque el nombre de archivo en comillas dobles o corchetes angulares.

El ejemplo siguiente genera C2006:

```
// C2006.cpp
#include stdio.h   // C2006
```

Posible resolución:

```
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```