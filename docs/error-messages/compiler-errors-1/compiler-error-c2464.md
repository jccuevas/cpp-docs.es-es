---
title: Error del compilador C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: a00ac997f73175eeab08a0132128e48e8fc58feb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338901"
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