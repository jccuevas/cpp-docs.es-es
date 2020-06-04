---
title: Advertencia del compilador (nivel 1) C4087
ms.date: 11/04/2016
f1_keywords:
- C4087
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
ms.openlocfilehash: d939edfdf00b81837a167ab326ab5a7791e3e374
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164019"
---
# <a name="compiler-warning-level-1-c4087"></a>Advertencia del compilador (nivel 1) C4087

'función': se ha declarado con la lista de parámetros 'void'.

La declaración de función no tiene parámetros formales, pero la llamada de función tiene parámetros reales. Se pasan parámetros adicionales según la convención de llamada de la función.

Esta advertencia es para el compilador de C.

## <a name="example"></a>Ejemplo

```c
// C4087.c
// compile with: /W1
int f1( void ) {
}

int main() {
   f1( 10 );   // C4087
}
```
