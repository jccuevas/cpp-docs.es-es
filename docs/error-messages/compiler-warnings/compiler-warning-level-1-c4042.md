---
title: ADVERTENCIA del compilador (nivel 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: db7f0425c3752c20ca8c5d4b6c95845ff64475c5
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627032"
---
# <a name="compiler-warning-level-1-c4042"></a>ADVERTENCIA del compilador (nivel 1) C4042

' Identifier ': tiene una clase de almacenamiento incorrecta

La clase de almacenamiento especificada no se puede usar con este identificador en este contexto. En su lugar, el compilador usa la clase de almacenamiento predeterminada:

- `extern`, si el *identificador* es una función.

- **auto**, si *Identifier* es un parámetro formal o una variable local.

- Sin clase de almacenamiento, si el *identificador* es una variable global.

Esta advertencia puede deberse a la especificación de una clase de almacenamiento distinta de **Register** en una declaración de parámetro.

En el ejemplo siguiente se genera C4042

```cpp
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```