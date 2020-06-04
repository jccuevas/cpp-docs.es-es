---
title: Error del compilador C2198
ms.date: 11/04/2016
f1_keywords:
- C2198
helpviewer_keywords:
- C2198
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
ms.openlocfilehash: cbe4f95037aabf3b4febc1a8fff5a324773a33b4
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301839"
---
# <a name="compiler-error-c2198"></a>Error del compilador C2198

'function': no hay suficientes argumentos para la llamada

El compilador no encontró parámetros suficientes para realizar una llamada a la función o detectó una declaración de función incorrecta.

El ejemplo siguiente genera la advertencia C2198:

```c
// C2198.c
// compile with: /c
void func( int, int );
int main() {
   func( 1 );   // C2198 only one actual parameter
   func( 1, 1 );   // OK
}
```
