---
title: Error del compilador C2548
ms.date: 11/04/2016
f1_keywords:
- C2548
helpviewer_keywords:
- C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
ms.openlocfilehash: f89208314c1d2e8ddb5100da72aa600a411b4608
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756804"
---
# <a name="compiler-error-c2548"></a>Error del compilador C2548

' Class:: Member ': falta el parámetro predeterminado para el parámetro Parameter

Falta un parámetro en la lista de parámetros predeterminada. Si proporciona un parámetro predeterminado en cualquier parte de una lista de parámetros, debe definir los parámetros predeterminados para todos los parámetros subsiguientes.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2548:

```cpp
// C2548.cpp
// compile with: /c
void func( int = 1, int, int = 3);  // C2548

// OK
void func2( int, int, int = 3);
void func3( int, int = 2, int = 3);
```
