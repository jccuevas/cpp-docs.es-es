---
title: Error del compilador C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 3766eaa83457ba6cffaf8b1599983a065772911c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750148"
---
# <a name="compiler-error-c3530"></a>Error del compilador C3530

' auto ' no se puede combinar con ningún otro especificador de tipo

Un especificador de tipo se usa con la palabra clave `auto`.

### <a name="to-correct-this-error"></a>Para corregir este error

1. No use un especificador de tipo en una declaración de variable que use la palabra clave `auto`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3530 porque la variable `x` se declara con la palabra clave `auto` y el tipo `int`, y porque el ejemplo se compila con **/Zc: auto**.

```cpp
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)
