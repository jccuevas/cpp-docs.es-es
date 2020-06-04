---
title: Error del compilador C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: e4952f4702d871ecf1c818b1fc7394e54a1a295f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743892"
---
# <a name="compiler-error-c2464"></a>Error del compilador C2464

' Identifier ': no se puede usar ' New ' para asignar una referencia

Se asignó un identificador de referencia con el operador `new`. Las referencias no son objetos de memoria, por lo que `new` no pueden devolver un puntero a ellas. Use la sintaxis de declaración de variable estándar para declarar una referencia.

En el ejemplo siguiente se genera C2464:

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
