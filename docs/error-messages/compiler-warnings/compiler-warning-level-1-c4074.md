---
title: ADVERTENCIA del compilador (nivel 1) C4074
ms.date: 11/04/2016
f1_keywords:
- C4074
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
ms.openlocfilehash: 1c84bbf436354ed672cedf13358837e298c7e4a5
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626915"
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