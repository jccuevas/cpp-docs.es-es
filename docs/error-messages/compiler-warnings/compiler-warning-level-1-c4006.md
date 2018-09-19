---
title: Del compilador (nivel 1) de la advertencia C4006 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4006
dev_langs:
- C++
helpviewer_keywords:
- C4006
ms.assetid: f1a59819-0fd2-4361-8e3a-99e4b514b8e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35987244498b95dfee6f285f100237c3d3a361ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037056"
---
# <a name="compiler-warning-level-1-c4006"></a>Advertencia del compilador (nivel 1) C4006

\#undef esperaba un identificador

La directiva `#undef` no especificó un identificador al que quitar la definición. Se omitió la directiva. Para resolver la advertencia, asegúrese de especificar un identificador. El ejemplo siguiente genera la advertencia C4006:

```
// C4006.cpp
// compile with: /W1
#undef   // C4006

// try..
// #undef TEST

int main() {
}
```