---
title: Error del compilador C2593 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2593
dev_langs:
- C++
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a3b0d1a8574aa5c05bbca023a1209cf1801f57e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042733"
---
# <a name="compiler-error-c2593"></a>Error del compilador C2593

'operador identificador' es ambiguo

Se define más de un operador para posibles para un operador sobrecargado.

Este error puede corregirse si usa una conversión explícita en uno o varios parámetros reales.

El ejemplo siguiente genera C2593:

```
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

Este error puede deberse a un punto flotante por medio de serializar un `CArchive` objeto. El compilador identifica la `<<` operador como ambigua. Tipos de C++ solo primitivos que `CArchive` puede serializar son los tipos de tamaño fijo `BYTE`, `WORD`, `DWORD`, y `LONG`. Todos los tipos de entero deben convertirse en uno de estos tipos para la serialización. Tipos de punto flotante pueden almacenarse utilizando el `CArchive::Write()` función miembro.

El ejemplo siguiente muestra cómo almacenar una variable de punto flotante (`f`) al archivo `ar`:

```
ar.Write(&f, sizeof( float ));
```