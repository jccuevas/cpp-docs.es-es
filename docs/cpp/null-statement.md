---
title: NULL instrucción | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27180a8252344f7b3185ec83b48ebef42f832907
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077365"
---
# <a name="null-statement"></a>NULL (Instrucción)

La "instrucción null" es una instrucción de expresión con el *expresión* que faltan. Es útil cuando la sintaxis del lenguaje llama a una instrucción pero no a una evaluación de la expresión. Consta de un punto y coma.

Las instrucciones null se utilizan normalmente como marcadores de posición en instrucciones de iteración o como instrucciones en las que se colocan etiquetas al final de las instrucciones compuestas o funciones.

El siguiente fragmento de código muestra cómo copiar una cadena a otra e incorpora la instrucción null:

```cpp
// null_statement.cpp
char *myStrCpy( char *Dest, const char *Source )
{
    char *DestStart = Dest;

    // Assign value pointed to by Source to
    // Dest until the end-of-string 0 is
    // encountered.
    while( *Dest++ = *Source++ )
        ;   // Null statement.

    return DestStart;
}

int main()
{
}
```

## <a name="see-also"></a>Vea también

[Expression (Instrucción)](../cpp/expression-statement.md)