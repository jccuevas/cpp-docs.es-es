---
title: Error del compilador C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: 40e666b1f2b566ca6309ee7759452647f8101a38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205249"
---
# <a name="compiler-error-c2457"></a>Error del compilador C2457

> '*macro*': la macro predefinida no puede aparecer fuera de un cuerpo de función

Ha intentado usar una macro predefinida, como [ &#95; &#95;function&#95;](../../preprocessor/predefined-macros.md), en un espacio global.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2457 y también se muestra el uso correcto:

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```
