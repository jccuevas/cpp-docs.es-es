---
title: Error del compilador C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 39f779ee846cf4f328f9c7af59ae394d97d7a3ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744737"
---
# <a name="compiler-error-c2422"></a>Error del compilador C2422

invalidación de segmento no válida en ' operando '

El código de ensamblado alineado usa incorrectamente un operador de invalidación de segmento (dos puntos) en un operando.  Las posibles causas son:

- El registro anterior al operador no es un registro de segmento.

- El registro anterior al operador no es el único registro de segmento en el operando.

- El operador de invalidación de segmento aparece dentro de un operador de direccionamiento indirecto (corchetes).

- La expresión que sigue al operador de invalidación de segmento no es un operando inmediato ni un operando de memoria.

En el ejemplo siguiente se genera C2422:

```cpp
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```
