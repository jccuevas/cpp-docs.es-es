---
title: Operadores de multiplicación y el operador de módulo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '%'
- /
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02d6d7d5d8f6c7dcce54e1dff54795b253d9d04a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106072"
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>Operadores de multiplicación y el operador de módulo

## <a name="syntax"></a>Sintaxis

```
expression * expression 
expression / expression 
expression % expression
```

## <a name="remarks"></a>Comentarios

Los operadores multiplicativos son:

- Multiplicación (<strong>\*</strong>)

- División (**/**)

- Módulo (resto de la división) (**%**)

Estos operadores binarios tienen asociatividad de izquierda a derecha.

Los operadores multiplicativos toman operandos de tipos aritméticos. El operador de módulo (**%**) tiene un requisito más estricto que sus operandos deben ser de tipo entero. (Para obtener el resto de una división de punto flotante, use la función de tiempo de ejecución, [fmod](../c-runtime-library/reference/fmod-fmodf.md).) Las conversiones descritas en [conversiones estándar](standard-conversions.md) se aplican a los operandos y el resultado es del tipo convertido.

El operador de multiplicación produce el resultado de multiplicar el primer operando por el segundo.

El operador de división produce el resultado de dividir el primer operando por el segundo.

El operador de módulo produce el resto proporcionado por la expresión siguiente, donde *e1* es el primer operando y *e2* es el segundo: *e1* -(*e1*  /  *e2*) \* *e2*, donde ambos operandos son de tipos enteros.

La división por 0 en una expresión de división o de módulo es indefinida y provoca un error en tiempo de ejecución. Por consiguiente, las expresiones siguientes generan resultados erróneos, indefinidos:

```cpp
i % 0
f / 0.0
```

Si ambos operandos de una multiplicación, una división o una expresión de módulo tienen el mismo signo, el resultado es positivo. De lo contrario, el resultado es negativo. El resultado del signo de una operación de módulo lo define la implementación.

> [!NOTE]
>  Como las conversiones realizadas por los operadores multiplicativos no proporcionan condiciones de desbordamiento o subdesbordamiento, la información puede perderse si el resultado de una operación multiplicativa no se puede representar en el tipo de los operandos después de la conversión.

**Específicos de Microsoft**

En Microsoft C++, el resultado de una expresión de módulo tiene siempre el mismo signo que el primer operando.

**FIN de Específicos de Microsoft**

Si la división calculada de dos enteros es inexacta y solo un operando es negativo, el resultado es el entero mayor (en magnitud, independientemente del signo) que es menor que el valor exacto que produciría la operación de división. Por ejemplo, el valor calculado de -11 / 3 es-3.666666666. El resultado de esa división entero es -3.

La relación entre los operadores multiplicativos está determinada por la identidad (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*.

## <a name="example"></a>Ejemplo

El siguiente programa muestra los operadores multiplicativos. Tenga en cuenta que ambos operandos de `10 / 3` debe convertirse explícitamente al tipo **float** para evitar el truncamiento para que ambos operandos son del tipo **float** antes de la división.

```cpp
// expre_Multiplicative_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   int x = 3, y = 6, z = 10;
   cout  << "3 * 6 is " << x * y << endl
         << "6 / 3 is " << y / x << endl
         << "10 % 3 is " << z % x << endl
         << "10 / 3 is " << (float) z / x << endl;
}
```

## <a name="see-also"></a>Vea también

[Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores de multiplicación de C](../c-language/c-multiplicative-operators.md)