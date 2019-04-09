---
title: Error del compilador C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: 7a567e4396999f98d9e9740db0acf951c443d525
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026310"
---
# <a name="compiler-error-c3533"></a>Error del compilador C3533

'type': un parámetro no puede tener un tipo que contiene 'auto'

No se puede declarar un parámetro de método o una plantilla con el `auto` palabra clave si el valor predeterminado [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) opción del compilador está en vigor.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Quitar el `auto` palabra clave de la declaración de parámetro.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3533 porque declara un parámetro de función con el `auto` palabra clave y se compila con **/Zc: Auto**.

```
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3533 en modo C ++ 14 porque declara un parámetro de plantilla con el `auto` palabra clave y se compila con **/Zc: Auto**. (En C ++ 17, esto es una definición de una plantilla de clase con un parámetro de plantilla sin tipo único cuyo tipo se deduce válida).

```
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Vea también

[auto (Palabra clave)](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (Deducir tipo de variable)](../../build/reference/zc-auto-deduce-variable-type.md)
