---
title: Compilador advertencia (nivel 1) C4215 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4215
dev_langs:
- C++
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 137a278452e9e3e204d761f0519c16541cfdb46e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094096"
---
# <a name="compiler-warning-level-1-c4215"></a>Advertencia del compilador (nivel 1) C4215

ha utilizado una extensión no estándar: long float

Tratan las extensiones de Microsoft (/Ze) **long float** como **doble**. Compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) no lo hace. Use **doble** para mantener la compatibilidad.

El ejemplo siguiente genera C4215:

```
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```