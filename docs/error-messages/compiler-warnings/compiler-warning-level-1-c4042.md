---
title: Compilador advertencia (nivel 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: 99f4f45aad82aa9898dad4cffb60b8e3311ddc9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576835"
---
# <a name="compiler-warning-level-1-c4042"></a>Compilador advertencia (nivel 1) C4042

'identifier': tiene la clase de almacenamiento incorrecta

La clase de almacenamiento especificada no se puede usar con este identificador en este contexto. El compilador usa la clase de almacenamiento predeterminada en su lugar:

- `extern`, si *identificador* es una función.

- **Auto**si *identificador* es un parámetro formal o una variable local.

- La clase sin almacenamiento si *identificador* es una variable global.

Esta advertencia puede deberse a que se especifica una clase de almacenamiento distinto **registrar** en una declaración de parámetro.

El ejemplo siguiente genera C4042

```
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```