---
title: Error del compilador C2947
ms.date: 11/04/2016
f1_keywords:
- C2947
helpviewer_keywords:
- C2947
ms.assetid: 6c056f62-ec90-4883-8a67-aeeb6ec13546
ms.openlocfilehash: 7056c13edca534701ffe82f0169897ea804f40d7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755361"
---
# <a name="compiler-error-c2947"></a>Error del compilador C2947

se esperaba ' > ' para terminar la construcción; se encontró ' syntax '

Es posible que una lista de argumentos genérica o de plantilla no se haya terminado correctamente.

C2947 también se puede generar mediante errores de sintaxis.

En el ejemplo siguiente se genera C2947:

```cpp
// C2947.cpp
// compile with: /c
template <typename T>=   // C2947
// try the following line instead
// template <typename T>
struct A {};
```
