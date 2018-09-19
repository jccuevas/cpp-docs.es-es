---
title: Error del compilador C2389 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2389
dev_langs:
- C++
helpviewer_keywords:
- C2389
ms.assetid: 6122dc81-4ee3-49a5-a67d-d867808c9bac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73809d0fdd94871ad282042cef22a233ced19a32
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113245"
---
# <a name="compiler-error-c2389"></a>Error del compilador C2389

'operador': operando no válido 'nullptr'

`nullptr` no puede ser un operando.

El ejemplo siguiente genera la advertencia C2389:

```
// C2389.cpp
// compile with: /clr
int main() {
   throw nullptr;   // C2389
}
```