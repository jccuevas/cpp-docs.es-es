---
title: Error del compilador C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: ef3e954987b84ea128342b38307769903df4b346
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740486"
---
# <a name="compiler-error-c3537"></a>Error del compilador C3537

' type ': no se puede convertir a un tipo que contiene ' auto '

No se puede convertir una variable en el tipo indicado porque el tipo contiene la palabra clave `auto` y la opción de compilador [/Zc: auto](../../build/reference/zc-auto-deduce-variable-type.md) predeterminada está en vigor.

## <a name="example"></a>Ejemplo

El código siguiente produce C3537 porque las variables se convierten a un tipo que contiene la palabra clave `auto`.

```cpp
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
