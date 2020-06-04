---
title: Error del compilador C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: f69d43bf50f5f13957e49d1e9ffa798a3db5a7b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754698"
---
# <a name="compiler-error-c2632"></a>Error del compilador C2632

' Type1 ' seguido de ' tipo2 ' no es válido

Este error puede producirse si falta código entre dos especificadores de tipo.

En el ejemplo siguiente se genera C2632:

```cpp
// C2632.cpp
int float i;   // C2632
```

Este error también se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003. `bool` es ahora un tipo adecuado. En versiones anteriores, `bool` era una definición de tipo y se podían crear identificadores con ese nombre.

En el ejemplo siguiente se genera C2632:

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Para resolver este error de modo que el código sea válido en las versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C++, cambie el nombre del identificador.
