---
title: Operadores de asignación | Microsoft Docs
ms.custom: ''
ms.date: 03/05/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- =
- '*='
- /=
- '%='
- +=
- -=
- <<=
- '>>='
- '&='
- ^=
- '|='
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], C++
- '&= operator'
- ^= operator
- += operator
- '>>= operator'
- '|= operator'
- operator>>=
- '*= operator'
- '%= operator'
- ^= operator
- operator >>=
- = operator
- -= operator
- /= operator
- <<= operator
ms.assetid: b028cf35-2ff1-4f14-9027-fd53ebec8aa0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1429bcb9f4002cb65cc14000d3bcf62004000566
ms.sourcegitcommit: b05cff71a8a6a8a4c7bbea1263fd0a711853f921
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307924"
---
# <a name="assignment-operators"></a>Operadores de asignación

## <a name="syntax"></a>Sintaxis

*expresión* *operador de asignación* *expresión*

*operador de asignación* : uno de<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>= * = o = % = +=-= \< \<= >> = & = ^ =   \|=</strong>

## <a name="remarks"></a>Comentarios

Los operadores de asignación almacenan un valor en el objeto designado por el operando izquierdo. Hay dos tipos de operaciones de asignación:

1. *asignación simple*, en que el valor del segundo operando se almacena en el objeto especificado por el primer operando.

1. *asignación compuesta*, en el que se realiza una aritmética, mayúsculas o una operación bit a bit antes de almacenar el resultado.

Todos los operadores de asignación de la tabla siguiente, salvo el operador =, son operadores de asignación compuesta.

### <a name="assignment-operators"></a>Operadores de asignación

|Operador|Significado|
|--------------|-------------|
|**=**|Almacena el valor del segundo operando en el objeto especificado por el primer operando (asignación simple).|
|**\*=**|Multiplica el valor del primer operando por el valor del segundo operando; almacena el resultado en el objeto especificado por el primer operando.|
|**/=**|Divide el valor del primer operando por el valor del segundo operando; almacena el resultado en el objeto especificado por el primer operando.|
|**%=**|Toma el módulo del primer operando especificado por el valor del segundo operando; almacena el resultado en el objeto especificado por el primer operando.|
|**+=**|Suma el valor del segundo operando al valor del primer operando; almacena el resultado en el objeto especificado por el primer operando.|
|**-=**|Resta el valor del segundo operando del valor del primer operando; almacena el resultado en el objeto especificado por el primer operando.|
|**<\<=**|Desplaza a la izquierda el valor del primer operando el número de bits especificado por el valor del segundo operando; almacena el resultado en el objeto especificado por el primer operando.|
|**>>=**|Desplaza a la derecha el valor del primer operando el número de bits especificado por el valor del segundo operando; almacena el resultado en el objeto especificado por el primer operando.|
|**&=**|Obtiene el AND bit a bit del primer y el segundo operandos; almacena el resultado en el objeto especificado por el primer operando.|
|**^=**|Obtiene el OR exclusivo bit a bit del primer y el segundo operandos; almacena el resultado en el objeto especificado por el primer operando.|
|**\|=**|Obtiene el OR inclusivo bit a bit del primer y el segundo operandos; almacena el resultado en el objeto especificado por el primer operando.|

**Palabras clave de operador**

Tres de los operadores de asignación compuesta tienen equivalentes de texto. Son estos:

|Operador|Equivalente|
|--------------|----------------|
|**&=**|`and_eq`|
|**\|=**|`or_eq`|
|**^=**|`xor_eq`|

Hay dos maneras de acceder a estas palabras clave de operador en los programas: incluir el archivo de encabezado `iso646.h`, o compilar con la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador (deshabilitar extensiones de lenguaje).

## <a name="example"></a>Ejemplo

```cpp
// expre_Assignment_Operators.cpp
// compile with: /EHsc
// Demonstrate assignment operators
#include <iostream>
using namespace std;
int main() {
   int a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555;

   a += b;      // a is 9
   b %= a;      // b is 6
   c >>= 1;      // c is 5
   d |= e;      // Bitwise--d is 0xFFFF

   cout  << "a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555" << endl
         << "a += b yields " << a << endl
         << "b %= a yields " << b << endl
         << "c >>= 1 yields " << c << endl
         << "d |= e yields " << hex << d << endl;
}
```

## <a name="simple-assignment"></a>Asignación simple

El operador de asignación simple (**=**) hace que el valor del segundo operando se almacene en el objeto especificado por el primer operando. Si ambos objetos son de tipos aritméticos, el operando derecho se convierte al tipo de la izquierda antes de almacenar el valor.

Objetos de **const** y **volátil** tipos pueden asignarse a valores l de tipos que son simplemente **volátil** o que ninguna de ellas son **const** ni **volátil**.

Asignación a los objetos de tipo de clase (estructura, unión y tipos de clase) se realiza mediante una función denominada `operator=`. El comportamiento predeterminado de esta función de operador es realizar una copia bit a bit; sin embargo, este comportamiento se puede modificar con operadores sobrecargados. Consulte [la sobrecarga de operadores](../cpp/operator-overloading.md) para obtener más información. Además, pueden tener tipos de clase *Copiar asignación* y *asignación de movimiento* operadores. Para obtener más información, consulte [copie constructores y operadores de asignación](copy-constructors-and-copy-assignment-operators-cpp.md) y [constructores de movimiento y operadores de asignación de movimiento](move-constructors-and-move-assignment-operators-cpp.md).

Un objeto de cualquier clase derivada sin ambigüedad de una clase base se puede asignar a un objeto de la clase base. Lo contrario no es cierto porque hay una conversión implícita de la clase derivada a la clase base, pero no de la clase base a la clase derivada. Por ejemplo:

```cpp
// expre_SimpleAssignment.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
class ABase
{
public:
    ABase() { cout << "constructing ABase\n"; }
};

class ADerived : public ABase
{
public:
    ADerived() { cout << "constructing ADerived\n"; }
};

int main()
{
    ABase aBase;
    ADerived aDerived;

    aBase = aDerived; // OK
    aDerived = aBase; // C2679
}
```

Las asignaciones a los tipos de referencia se comportan como si la asignación se creara en el objeto al que señala la referencia.

Para los objetos de tipo de clase, la asignación es diferente de la inicialización. Para ver lo diferentes que pueden ser la asignación y la inicialización, considere el código

```cpp
UserType1 A;
UserType2 B = A;
```

El código anterior muestra un inicializador; llama al constructor para `UserType2` que toma un argumento de tipo `UserType1`. Dado el código

```cpp
UserType1 A;
UserType2 B;

B = A;
```

la instrucción de asignación

```cpp
B = A;
```

puede tener uno de los efectos siguientes:

- Llame a la función `operator=` para `UserType2`, que proporciona `operator=` viene con un `UserType1` argumento.

- Llamar a la función de conversión explícita `UserType1::operator UserType2`, si existe tal función.

- Llamar a un constructor `UserType2::UserType2`, siempre que exista un constructor de ese tipo, que tome un argumento `UserType1` y copie el resultado.

## <a name="compound-assignment"></a>Asignación compuesta

Los operadores de asignación compuesta, se muestra en la tabla de [operadores de asignación](#assignment-operators), se especifican en el formulario *e1* *op*= *e2*, donde *e1* es un valor l modificable no de **const** tipo y *e2* es uno de los siguientes:

- Un tipo aritmético

- Un puntero, si *op* es **+** o **-**

El *e1* *op*= *e2* formulario se comporta como *e1* **=** *e1* *op* *e2*, pero *e1* se evalúa solo una vez.

La asignación compuesta a un tipo enumerado genera un mensaje de error. Si el operando izquierdo tiene el tipo de puntero, el operando derecho debe tener el tipo de puntero o debe ser una expresión de constante que se evalúa como 0. Si el operando izquierdo tiene el tipo entero, el operando derecho no debe tener un tipo de puntero.

## <a name="result-of-assignment-operators"></a>Resultado de los operadores de asignación

Los operadores de asignación devuelven el valor del objeto especificado por el operando izquierdo después de la asignación. El tipo resultante es el tipo del operando izquierdo. El resultado de una expresión de asignación es siempre un valor L. Estos operadores tienen asociatividad de derecha a izquierda. El operando izquierdo debe ser un valor L modificable.

En ANSI C, el resultado de una expresión de asignación no es un valor L. Por lo tanto, la expresión `(a += b) += c` válida en C++ no lo es en C.

## <a name="see-also"></a>Vea también

[Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores de asignación de C](../c-language/c-assignment-operators.md)
