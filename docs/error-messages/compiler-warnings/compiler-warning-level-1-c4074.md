---
title: ADVERTENCIA del compilador (nivel 1) C4074
ms.date: 11/04/2016
f1_keywords:
- C4074
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
ms.openlocfilehash: 7a11112962872788df855bfc63b869193188fab9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164084"
---
# <a name="compiler-warning-level-1-c4074"></a>ADVERTENCIA del compilador (nivel 1) C4074

inicializadores put en el área de inicialización reservada del compilador

Microsoft reserva el área de inicialización del compilador, que se especifica mediante [#pragma init_seg](../../preprocessor/init-seg.md). El código de esta área se puede ejecutar antes de la inicialización de la biblioteca en tiempo de ejecución de C.

En el ejemplo siguiente se genera C4074:

```cpp
// C4074.cpp
// compile with: /W1
#pragma init_seg( compiler )   // C4074

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```
