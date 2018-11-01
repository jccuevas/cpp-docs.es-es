---
title: Error del compilador C2448
ms.date: 11/04/2016
f1_keywords:
- C2448
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
ms.openlocfilehash: 915217ffbe848b2814e9960183854e09a80b9ee8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434858"
---
# <a name="compiler-error-c2448"></a>Error del compilador C2448

'identifier': inicializador de estilo de función parece ser una definición de función

La definición de función no es correcta.

Este error puede deberse a una lista formal del lenguaje C de estilo antiguo.

El ejemplo siguiente genera C2448:

```
// C2448.cpp
void func(c)
   int c;
{}   // C2448
```