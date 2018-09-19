---
title: Error del compilador C3537 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3537
dev_langs:
- C++
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f04500998adf132594b91fc38f82c8bec4b1c5c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107697"
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