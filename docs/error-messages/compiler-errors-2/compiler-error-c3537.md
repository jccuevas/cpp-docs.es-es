---
title: Error del compilador C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: 50a06180dabfa192292fae7ba1962b6b7455bb89
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375930"
---
# <a name="compiler-error-c3537"></a>Error del compilador C3537

'type': no se puede convertir a un tipo que contiene 'auto'

No se puede convertir una variable para el tipo indicado porque el tipo contiene el `auto` palabra clave y el valor predeterminado [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) opción del compilador está en vigor.

## <a name="example"></a>Ejemplo

El código siguiente genera el error C3537 porque las variables se convierten en un tipo que contiene el `auto` palabra clave.

```
// C3537.cpp
// Compile with /Zc:auto
int main()
{
   int value = 123;
   auto(value);                        // C3537
   (auto)value;                        // C3537
   auto x1 = auto(value);              // C3537
   auto x2 = (auto)value;              // C3537
   auto x3 = static_cast<auto>(value); // C3537
   return 0;
}
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)