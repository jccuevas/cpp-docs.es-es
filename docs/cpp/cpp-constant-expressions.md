---
title: Expresiones constantes de C++
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: 97059066adadc3a7897cbd2c4c747e2a673e7201
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576429"
---
# <a name="c-constant-expressions"></a>Expresiones constantes de C++

Un *constante* valor es uno que no cambia. C++ proporciona dos palabras clave para que pueda expresar la intención de que un objeto no está pensado para ser modificado y aplicar dicha intención.

C++ requiere expresiones constantes —expresiones que se evalúan como una constante— para las declaraciones de:

- Límites de matrices

- Selectores en instrucciones case

- Especificación de longitud de campo de bits

- Inicializadores de enumeración

Los únicos operandos que son válidos en expresiones constantes son:

- Literales

- Constantes de enumeración

- Valores declarados como const que se inicializan con expresiones constantes

- **sizeof** expresiones

Las constantes no íntegras deben convertirse (explícita o implícitamente) en tipos enteros para ser válidos en una expresión constante. Por consiguiente, el código siguiente es legal.

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Las conversiones explícitas a tipos enteros son legales en expresiones constantes; todos los otros tipos y tipos derivados no son válidos excepto cuando se utilizan como operandos para el **sizeof** operador.

El operador de coma y los operadores de asignación no se pueden utilizar en expresiones constantes.

## <a name="see-also"></a>Vea también

[Tipos de expresiones](../cpp/types-of-expressions.md)