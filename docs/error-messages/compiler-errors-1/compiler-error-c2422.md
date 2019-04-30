---
title: Error del compilador C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 524eeadb6cf066d3eba3a7e88c45a9e2b993c0ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402897"
---
# <a name="compiler-error-c2422"></a>Error del compilador C2422

invalidación de segmento no válido en 'operando'

Código de ensamblado alineado utiliza incorrectamente un operador de invalidación de segmento (dos puntos) en un operando.  Entre las posibles causas se incluyen:

- El registro que precede al operador no es un registro de segmento.

- El registro que precede al operador no es el registro de segmento solo en el operando.

- El operador de invalidación de segmento aparece dentro de un operador de direccionamiento indirecto (paréntesis).

- La expresión que sigue al operador de invalidación de segmento no es un operando inmediato o un operando de memoria.

El ejemplo siguiente genera C2422:

```
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```