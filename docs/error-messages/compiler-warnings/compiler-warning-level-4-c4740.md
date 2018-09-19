---
title: Compilador advertencia (nivel 4) C4740 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4740
dev_langs:
- C++
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6353ac464d95e8805a9c9e55488a355f71372508
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056162"
---
# <a name="compiler-warning-level-4-c4740"></a>Advertencia del compilador (nivel 4) C4740

flujo dentro o fuera del código inline asm suprime la optimización global

Cuando hay un salto en a o fuera de un `asm` bloque, se deshabilitan las optimizaciones globales para esa función.

El ejemplo siguiente genera C4740:

```
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```