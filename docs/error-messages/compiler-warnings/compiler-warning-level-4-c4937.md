---
title: Advertencia del compilador (nivel 4) C4937
ms.date: 11/04/2016
f1_keywords:
- C4937
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
ms.openlocfilehash: dd7a7f9ac3d0ce0798a88f753cb0ccb4addbd5bc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988756"
---
# <a name="compiler-warning-level-4-c4937"></a>Advertencia del compilador (nivel 4) C4937

'texto1' y 'texto2' no se pueden distinguir como argumentos para 'directiva'

Debido a la forma en que el compilador procesa argumentos para directivas, no es posible distinguir los nombres que tienen un significado para el compilador como, por ejemplo, palabras clave con varias representaciones de texto (en formato de subrayado simple y doble).

Algunos ejemplos de estas cadenas son __cdecl y \__forceinline.  Tenga en cuenta que con /Za solo se habilita el formato de subrayado doble.

El ejemplo siguiente genera la advertencia C4937:

```cpp
// C4937.cpp
// compile with: /openmp /W4
#include "omp.h"
int main() {
   #pragma omp critical ( __leave )   // C4937
   ;

   // OK
   #pragma omp critical ( leave )
   ;
}
```
