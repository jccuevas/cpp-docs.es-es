---
title: Expresiones constantes de C++
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: d4d9803c7f80caba3c33d011e4df433491b9b591
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170584"
---
# <a name="c-constant-expressions"></a>Expresiones constantes de C++

Un valor *constante* es aquel que no cambia. C++ proporciona dos palabras clave para que pueda expresar la intención de que un objeto no está pensado para ser modificado y aplicar dicha intención.

C++ requiere expresiones constantes —expresiones que se evalúan como una constante— para las declaraciones de:

- Límites de matrices

- Selectores en instrucciones case

- Especificación de longitud de campo de bits

- Inicializadores de enumeración

Los únicos operandos que son válidos en expresiones constantes son:

- Literales

- Constantes de enumeración

- Valores declarados como const que se inicializan con expresiones constantes

- expresiones **sizeof**

Las constantes no íntegras deben convertirse (explícita o implícitamente) en tipos enteros para ser válidos en una expresión constante. Por consiguiente, el código siguiente es legal.

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Las conversiones explícitas a tipos enteros son legales en expresiones constantes; el resto de tipos y los tipos derivados no son válidos excepto cuando se utilizan como operandos para el operador **sizeof** .

El operador de coma y los operadores de asignación no se pueden utilizar en expresiones constantes.

## <a name="see-also"></a>Consulte también

[Tipos de expresiones](../cpp/types-of-expressions.md)
