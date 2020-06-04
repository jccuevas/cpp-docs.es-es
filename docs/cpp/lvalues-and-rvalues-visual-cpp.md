---
title: 'Categorías de valor: Lvalues y RvaluesC++()'
ms.date: 05/07/2019
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 23625ddf44d16a4dc408b87f27b9cdfba7a9cbd4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077235"
---
# <a name="lvalues-and-rvalues-c"></a>Lvalues y rvalues (C++)

Cada C++ expresión tiene un tipo y pertenece a una *categoría de valor*. Las categorías de valor son la base de las reglas que deben seguir los compiladores al crear, copiar y mover objetos temporales durante la evaluación de expresiones.

El estándar C++ 17 define las categorías de valores de expresión de la manera siguiente:

- Un *glvalue* es una expresión cuya evaluación determina la identidad de un objeto, un campo de bits o una función.
- Un *prvalue* es una expresión cuya evaluación Inicializa un objeto o un campo de bits, o calcula el valor del operando de un operador, según se especifica en el contexto en el que aparece.
- Un *xValue* es un glvalue que denota un objeto o un campo de bits cuyos recursos se pueden reutilizar (normalmente porque está cerca del final de su duración). Ejemplo: ciertos tipos de expresiones que afectan a las referencias rvalue (8.3.2) producen xvalues, como una llamada a una función cuyo tipo de valor devuelto es una referencia rvalue o una conversión a un tipo de referencia rvalue.
- Un valor *l* es un glvalue que no es un xValue.
- Un valor *r* es un prvalue o un xValue.

En el siguiente diagrama se muestran las relaciones entre las categorías:

![C++categorías de valores de expresión](media/value_categories.png "C++categorías de valores de expresión")

Un valor l tiene una dirección a la que el programa puede tener acceso. Los ejemplos de expresiones lvalue incluyen nombres de variable, incluidas variables **const** , elementos de matriz, llamadas de función que devuelven una referencia lvalue, campos de bits, uniones y miembros de clase.

Una expresión prvalue no tiene ninguna dirección a la que pueda acceder el programa. Entre los ejemplos de expresiones prvalue se incluyen los literales, las llamadas de función que devuelven un tipo sin referencia y los objetos temporales que se crean durante la evaluación de la expresión, pero solo el compilador puede acceder a ellos.

Una expresión xValue tiene una dirección que ya no es accesible para el programa, pero se puede usar para inicializar una referencia rvalue, que proporciona acceso a la expresión. Entre los ejemplos se incluyen las llamadas a funciones que devuelven una referencia rvalue y las expresiones subscript, miembro y puntero a miembro de matriz, donde la matriz o el objeto es una referencia rvalue.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran varios usos correctos e incorrectos de valores L y valores R:

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
    int i, j, *p;

    // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
    i = 7;

    // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
    7 = i; // C2106
    j * 4 = 7; // C2106

    // Correct usage: the dereferenced pointer is an lvalue.
    *p = i;

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;

    // Incorrect usage: the constant ci is a non-modifiable lvalue (C3892).
    const int ci = 7;
    ci = 9; // C3892
}
```

> [!NOTE]
> En los ejemplos de este tema se muestra el uso correcto e incorrecto cuando los operadores no están sobrecargados. Si sobrecarga operadores, puede convertir una expresión tal como `j * 4` en un valor L.

Los términos *lvalue* y *rvalue* se suelen usar cuando se hace referencia a referencias a objetos. Para obtener más información sobre las referencias, vea [declarador de referencia de valor l: &](../cpp/lvalue-reference-declarator-amp.md) y [declarador de referencia de valor r: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Consulte también

[Conceptos básicos](../cpp/basic-concepts-cpp.md)<br/>
[Declarador de referencia a un valor L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md)
