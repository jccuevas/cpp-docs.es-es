---
title: Error del compilador C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: a00ac997f73175eeab08a0132128e48e8fc58feb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498194"
---
# <a name="compiler-error-c2464"></a>Error del compilador C2464

'identifier': no se puede utilizar 'new' para asignar una referencia

Se ha asignado un identificador de referencia con el `new` operador. Las referencias no son objetos de memoria, por lo que `new` no puede devolver un puntero a ellos. Use la sintaxis de declaración de variable estándar para declarar una referencia.

El ejemplo siguiente genera C2464:

```
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```