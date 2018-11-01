---
title: Advertencia del compilador (nivel 1) C4615
ms.date: 11/04/2016
f1_keywords:
- C4615
helpviewer_keywords:
- C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
ms.openlocfilehash: 1032261c39e0a285ac686e09573161de3b46e0e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573532"
---
# <a name="compiler-warning-level-1-c4615"></a>Advertencia del compilador (nivel 1) C4615

\#advertencia pragma: tipo de advertencia de usuario desconocido

Se usó un especificador de advertencia no válido con **pragma** [advertencia](../../preprocessor/warning.md). Para resolver el error, utilice un especificador de advertencia válido.

El ejemplo siguiente genera C4615:

```
// C4615.cpp
// compile with: /W1 /LD
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier

// use the code below to resolve the error
// #pragma warning(default : 4401)
```