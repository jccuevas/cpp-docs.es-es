---
title: Error irrecuperable C1018 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1018
dev_langs:
- C++
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5549cdd40b8287f75f80b0e633ff053a23cdecde
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034452"
---
# <a name="fatal-error-c1018"></a>Error irrecuperable C1018

#elif inesperada

La directiva `#elif` aparece fuera de una construcción `#if`, `#ifdef`o `#ifndef` . Use `#elif` solamente dentro de una de estas construcciones.

El ejemplo siguiente genera la advertencia C1018:

```
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

Posible solución:

```
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```