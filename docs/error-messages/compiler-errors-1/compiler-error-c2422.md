---
title: Error del compilador C2422 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17421f2d4a7823c0e2fbb34a54a7c562223c798c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047036"
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