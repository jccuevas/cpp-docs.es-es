---
title: return (instrucción) finalización del programa (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfcf65258767178c0f74f63ca6e938e1d940e3be
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061141"
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