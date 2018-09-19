---
title: Del compilador (nivel 3) de la advertencia C4018 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4018
dev_langs:
- C++
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99ca94a47925a64c91077ad5b363e953def186b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041329"
---
# <a name="compiler-warning-level-3-c4018"></a>Del compilador (nivel 3) de la advertencia C4018

'expresión': no coinciden signed/unsigned

Comparación de un número con signo y sin signo necesarios al compilador que convierta el valor con signo en tipos sin signo.

Esta advertencia puede corregirse si se convierte uno de los dos tipos al probar los tipos con signo y sin signo.

El ejemplo siguiente genera C4018:

```
// C4018.cpp
// compile with: /W3
int main() {
   unsigned int uc = 0;
   int c = 0;
   unsigned int c2 = 0;

   if (uc < c) uc = 0;   // C4018

   // OK
   if (uc == c2) uc = 0;
}
```