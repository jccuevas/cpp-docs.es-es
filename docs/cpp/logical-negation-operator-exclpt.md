---
title: 'Operador lógico de negación: !'
ms.date: 08/27/2018
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 06142ef15fcdbafdbae4b892772a04b117c087f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446538"
---
# <a name="logical-negation-operator-"></a>Operador lógico de negación: !

## <a name="syntax"></a>Sintaxis

```
! cast-expression
```

## <a name="remarks"></a>Observaciones

El operador lógico de negación ( **!** ) invierte el significado de su operando. El operando debe ser de tipo aritmético o de puntero (o una expresión que se evalúe como un tipo aritmético o de puntero). El operando se convierte implícitamente al tipo **bool**. El resultado es TRUE si el operando convertido es FALSE; el resultado es FALSE si el operando convertido es TRUE. El resultado es de tipo **bool**.

En el caso de una expresión *e*, la expresión unaria `!e` es equivalente a la expresión `(e == 0)`, excepto en los casos en los que intervienen los operadores sobrecargados.

## <a name="operator-keyword-for-"></a>Palabra clave del operador para !

El operador **Not** es una ortografía alternativa de **!** . Hay dos maneras de tener acceso al operador **Not** en los programas: incluir el archivo de encabezado \<iso646. h > o compilar con la opción del compilador [/za](../build/reference/za-ze-disable-language-extensions.md) (deshabilitar extensiones de lenguaje).

## <a name="example"></a>Ejemplo

```cpp
// expre_Logical_NOT_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    if (!i)
        cout << "i is zero" << endl;
}
```

## <a name="see-also"></a>Consulte también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores aritméticos unarios](../c-language/unary-arithmetic-operators.md)<br/>
