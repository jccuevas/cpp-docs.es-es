---
title: Del compilador (nivel 4) de la advertencia C4932 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4932
dev_langs:
- C++
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c9143406fc4b52d50b5dc68215fa796f5100fb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053926"
---
# <a name="compiler-warning-level-4-c4932"></a>Advertencia del compilador (nivel 4) C4932

__identifier (identifier) y \__identifier(identifier) son indistinguibles

El compilador es no puede distinguir entre **_finally** y `__finally` o entre `__try` y **_try** como parámetro pasado a [__identifier](../../windows/identifier-cpp-cli.md). No debería intentar usar ambos como identificadores en el mismo programa, ya que provocarán un error [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) .

El ejemplo siguiente genera la advertencia C4932:

```
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```