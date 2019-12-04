---
title: Error del compilador C3106
ms.date: 11/04/2016
f1_keywords:
- C3106
helpviewer_keywords:
- C3106
ms.assetid: 39d97a32-0905-4702-87d3-7f8ce473fb93
ms.openlocfilehash: 85aef1937ccbdbbbc335e4166fab11aa982b1839
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755842"
---
# <a name="compiler-error-c3106"></a>Error del compilador C3106

' atributo ': los argumentos sin nombre deben preceder a los argumentos con nombre

Los argumentos sin nombre se deben pasar a un atributo antes que los argumentos con nombre.

Para obtener más información, consulta [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3106.

```cpp
// C3106.cpp
// compile with: /c
[module(name="MyLib", dll)];   // C3106
[module(dll, name="MyLib")];   // OK
```
