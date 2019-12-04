---
title: Error del compilador C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: ce95bba417e9be3603f15376a0fd65a48f951a2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755647"
---
# <a name="compiler-error-c3533"></a>Error del compilador C3533

' type ': un parámetro no puede tener un tipo que contiene ' auto '

Un parámetro de método o plantilla no se puede declarar con la palabra clave `auto` si la opción del compilador [/Zc: auto](../../build/reference/zc-auto-deduce-variable-type.md) predeterminada está en vigor.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Quite la palabra clave `auto` de la declaración del parámetro.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3533 porque declara un parámetro de función con la palabra clave `auto` y se compila con **/Zc: auto**.

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3533 en modo C++ 14 porque declara un parámetro de plantilla con la palabra clave `auto` y se compila con **/Zc: auto**. (En C++ 17, se trata de una definición válida de una plantilla de clase con un solo parámetro de plantilla sin tipo cuyo tipo se deduce).

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Deducir tipo de variable)](../../build/reference/zc-auto-deduce-variable-type.md)
