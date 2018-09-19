---
title: hacer-while (instrucción (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- do_cpp
dev_langs:
- C++
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37155be11caaee9c609a0e11ddbfeb5d62856903
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071203"
---
# <a name="do-while-statement-c"></a>do-while (instrucción de C++)

Ejecuta un *instrucción* repetidamente hasta que la condición de finalización (el *expresión*) se evalúa como cero.

## <a name="syntax"></a>Sintaxis

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Comentarios

La prueba de la condición de finalización se realiza después de cada ejecución del bucle; por lo tanto, un **hacer-mientras** bucle ejecuta una o varias veces, dependiendo del valor de la expresión de finalización. La instrucción **do-while** también puede finalizar cuando se ejecuta una instrucción [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md) o [return](../cpp/return-statement-cpp.md) dentro del cuerpo de la instrucción.

*expression* debe tener un tipo aritmético o de puntero. La ejecución continúa de la siguiente manera:

1. Se ejecuta el cuerpo de instrucción.

1. A continuación, se evalúa *expression*. Si *expression* es false, la instrucción **do-while** finaliza y el control pasa a la siguiente instrucción del programa. Si *expression* es true (distinta de cero), el proceso se repite a partir del paso 1.

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra el **hacer-mientras** instrucción:

```cpp
// do_while_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        printf_s("\n%d",i++);
    } while (i < 3);
}
```

## <a name="see-also"></a>Vea también

[Instrucciones de iteración](../cpp/iteration-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[while (Instrucción) (C++)](../cpp/while-statement-cpp.md)<br/>
[for (Instrucción) (C++)](../cpp/for-statement-cpp.md)<br/>
[Instrucción for basada en intervalo (C++)](../cpp/range-based-for-statement-cpp.md)