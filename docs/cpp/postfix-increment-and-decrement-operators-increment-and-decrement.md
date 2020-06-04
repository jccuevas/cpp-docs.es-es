---
title: 'Operadores de incremento y decremento postfijos: ++ y --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
ms.openlocfilehash: 44b1031376abd6c50c3b9706089042995994e495
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177682"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Operadores de incremento y decremento postfijos: ++ y --

## <a name="syntax"></a>Sintaxis

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>Observaciones

C++ proporciona operadores de incremento y decremento tanto de prefijo como de postfijo. En esta sección, se describen solo los de postfijo. (Para obtener más información, vea [operadores de incremento y decremento prefijos](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)). La diferencia entre los dos es que, en la notación de postfijo, el operador aparece después de *postfijo-Expression*, mientras que, en la notación de prefijo, el operador aparece antes de la *expresión.* En el ejemplo siguiente, se muestra un operador de incremento de postfijo:

```cpp
i++;
```

El efecto de aplicar el operador de incremento de postfijo ( **++** ) es que el valor del operando se incrementa en una unidad del tipo adecuado. Del mismo modo, el efecto de aplicar el operador de decremento de postfijo ( **--** ) es que el valor del operando se reduce en una unidad del tipo adecuado.

Es importante tener en cuenta que una expresión de incremento o decremento de postfijo se evalúa como el valor de la expresión *antes* de la aplicación del operador respectivo. La operación de incremento o decremento se produce *después* de evaluarse el operando. El problema surge solo cuando la operación de incremento o decremento de postfijo se da en el contexto de una expresión mayor.

Cuando se aplica un operador de postfijo a un argumento de función, no es seguro que el valor del argumento aumente o disminuya antes de que se pase a la función.  Para obtener más información, vea la sección 1.9.17 del estándar C++.

Al aplicar el operador de incremento de postfijo a un puntero a una matriz de objetos de tipo **Long** , en realidad se agregan cuatro a la representación interna del puntero. Este comportamiento hace que el puntero, que anteriormente hacía referencia al elemento *n*de la matriz, haga referencia al elemento (*n*+ 1) TH.

Los operandos de los operadores de incremento de postfijo y de decremento de postfijo deben ser valores l modificables (no **const**) de tipo aritmético o de puntero. El tipo del resultado es el mismo que el de la *expresión de postfijo*, pero ya no es un valor l.

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): el operando de un operador de incremento o decremento postfijo no puede ser de tipo **bool**.

El código siguiente muestra el operador de incremento de postfijo:

```cpp
// expre_Postfix_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
   int i = 10;
   cout << i++ << endl;
   cout << i << endl;
}
```

No se admiten las operaciones de incremento y decremento de postfijo en los tipos enumerados:

```cpp
enum Compass { North, South, East, West );
Compass myCompass;
for( myCompass = North; myCompass != West; myCompass++ ) // Error
```

## <a name="see-also"></a>Consulte también

[Expresiones postfijas](../cpp/postfix-expressions.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores de incremento y decremento postfijos de C](../c-language/c-postfix-increment-and-decrement-operators.md)
