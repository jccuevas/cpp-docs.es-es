---
title: Compilador advertencia (nivel 2) C4056 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4056
dev_langs:
- C++
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e069867d4aef749f9f6e42f46a34745d9e8aa62
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067512"
---
# <a name="compiler-warning-level-2-c4056"></a>Compilador advertencia (nivel 2) C4056

desbordamiento en la aritmética de constante de punto flotante

Aritmética de constante de punto flotante, genera un resultado que supera el valor máximo permitido.

Esta advertencia puede deberse a optimizaciones del compilador durante la aritmética de constante. Puede ignorar esta advertencia si desaparece al desactivar la optimización ([/Od](../../build/reference/od-disable-debug.md)).

El ejemplo siguiente genera C4056:

```
// C4056.cpp
// compile with: /W2 /LD
#pragma warning (default : 4056)
float fp_val = 1.0e300 * 1.0e300;   // C4056
```