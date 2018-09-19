---
title: Del compilador (nivel 4) de la advertencia C4343 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4343
dev_langs:
- C++
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bb524afda167333d4df97089402040496a7a944
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071060"
---
# <a name="compiler-warning-level-4-c4343"></a>Advertencia del compilador (nivel 4) C4343

\#pragma optimize("g",off) invalida la opción /Og

Esta advertencia, solo válida en el compilador de la familia de procesadores Itanium (IPF), informa de que una directiva pragma [optimize](../../preprocessor/optimize.md) reemplazó una opción del compilador [/Og](../../build/reference/og-global-optimizations.md) .

El ejemplo siguiente genera la advertencia C4343:

```
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```