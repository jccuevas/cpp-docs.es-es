---
title: Error del compilador C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: a08ac9f9cfbc332b90ad16c663349ee227427278
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446645"
---
# <a name="compiler-error-c2457"></a>Error del compilador C2457

> '*macro*': la macro predefinida no puede aparecer fuera de un cuerpo de función

Se intentó utilizar una macro predefinida, como [ &#95; &#95;función&#95;&#95;](../../preprocessor/predefined-macros.md), en un espacio global.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2457 y también muestra el uso correcto:

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```