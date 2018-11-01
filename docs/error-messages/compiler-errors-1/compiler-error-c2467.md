---
title: Error del compilador C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: aa45cbb19519dea7bd5c8fb96abd2c76ea30a786
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598034"
---
# <a name="compiler-error-c2467"></a>Error del compilador C2467

declaración no válida de 'usuario-definido-tipo anónimo'

Se ha declarado un tipo anidado definido por el usuario. Este es un error al compilar código fuente C con la opción de compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) habilitado.

El ejemplo siguiente genera C2467:

```
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```