---
title: Error del compilador C2198
ms.date: 11/04/2016
f1_keywords:
- C2198
helpviewer_keywords:
- C2198
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
ms.openlocfilehash: a7fbc5dc6dc91dab5bfea3a81c8d5c045e485161
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182826"
---
# <a name="compiler-error-c2198"></a>Error del compilador C2198

'function': no hay suficientes argumentos para la llamada

El compilador no encontró parámetros suficientes para realizar una llamada a la función o detectó una declaración de función incorrecta.

El ejemplo siguiente genera la advertencia C2198:

```
// C2198.c
// compile with: /c
void func( int, int );
int main() {
   func( 1 );   // C2198 only one actual parameter
   func( 1, 1 );   // OK
}
```