---
title: Advertencia del compilador (nivel 1) C4081
ms.date: 11/04/2016
f1_keywords:
- C4081
helpviewer_keywords:
- C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
ms.openlocfilehash: f43a736a73b4a504755cd8dc079a41e59aaf72bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624658"
---
# <a name="compiler-warning-level-1-c4081"></a>Advertencia del compilador (nivel 1) C4081

se esperaba 'token1'; se encontró 'token2'

El compilador esperaba un token distinto en este contexto.

## <a name="example"></a>Ejemplo

```
// C4081.cpp
// compile with: /W1 /LD
#pragma optimize) "l", on )   // C4081
```