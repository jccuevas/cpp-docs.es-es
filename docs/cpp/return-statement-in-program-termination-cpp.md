---
title: return (Instrucción de finalización del programa) (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
ms.openlocfilehash: 9c7b6130ee1a0b49ab75a70d84764d3a1f8c5ef0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613050"
---
# <a name="return-statement-in-program-termination-c"></a>return (Instrucción de finalización del programa) (C++)

Emitir un **devolver** instrucción desde `main` es funcionalmente equivalente a llamar a la `exit` función. Considere el ejemplo siguiente:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

El `exit` y **devolver** instrucciones en el ejemplo anterior son funcionalmente idénticas. Sin embargo, C++ requiere que las funciones que tienen devuelven tipos diferentes de **void** devuelven un valor. El **devolver** instrucción permite devolver un valor de `main`.

## <a name="see-also"></a>Vea también

[Finalización del programa](../cpp/program-termination.md)