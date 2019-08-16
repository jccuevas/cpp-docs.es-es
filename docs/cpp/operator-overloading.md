---
title: Sobrecarga de operadores
ms.date: 11/04/2016
f1_keywords:
- operator_cpp
- operator
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
ms.openlocfilehash: d6a294af3ea7ef6085eae0f7069ea2d1fdbb30e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377366"
---
# <a name="operator-overloading"></a>Sobrecarga de operadores

El **operador** palabra clave declara una función especificando qué *símbolo de operador* significa que cuando se aplica a las instancias de una clase. Esto proporciona al operador más de un significado, o lo "sobrecarga". El compilador distingue entre los diferentes significados de un operador examinando los tipos de sus operandos.

## <a name="syntax"></a>Sintaxis

> *type* **operator** *operator-symbol* **(** *parameter-list* **)**

## <a name="remarks"></a>Comentarios

Se puede redefinir la función de la mayoría de los operadores integrados de forma global o clase a clase. Los operadores sobrecargados se implementan como funciones.

El nombre de un operador sobrecargado es **operador** *x*, donde *x* es el operador tal como aparece en la tabla siguiente. Por ejemplo, para sobrecargar el operador de suma, definir una función denominada **operator +**. De forma similar, para sobrecargar el operador de suma y asignación, **+=**, definir una función denominada **operador +=**.

### <a name="redefinable-operators"></a>Operadores redefinibles

|Operador|Name|Tipo|
|--------------|----------|----------|
|**,**|Coma|Binary|
|**\!**|NOT lógico|Unario|
|**\!=**|Desigualdad|Binary|
|**%**|Módulo|Binary|
|**%=**|Asignación y módulo|Binary|
|**&**|AND bit a bit|Binary|
|**&**|Dirección de|Unario|
|**&&**|AND lógico|Binary|
|**&=**|Asignación AND bit a bit|Binary|
|**( )**|Llamada a función|—|
|**( )**|Operador de conversión|Unario|
|**&#42;**|Multiplicación|Binary|
|**&#42;**|Desreferencia de puntero|Unario|
|**&#42;=**|Asignación y multiplicación|Binary|
|**+**|Adición|Binary|
|**+**|Unario más|Unario|
|**++**|Incremento <sup>1</sup>|Unario|
|**+=**|Asignación y suma|Binary|
|**-**|Resta|Binary|
|**-**|Negación unaria|Unario|
|**--**|Decremento <sup>1</sup>|Unario|
|**-=**|Asignación y resta|Binary|
|**->**|Selección de miembro|Binary|
|**->&#42;**|Selección de puntero a miembro|Binary|
|**/**|División|Binary|
|**/=**|Asignación y división|Binary|
|**\<**|Menor que|Binary|
|**<<**|Desplazamiento a la izquierda|Binary|
|**<<=**|Asignación y desplazamiento a la izquierda|Binary|
|**<=**|Menor o igual que|Binary|
|**=**|Asignación|Binary|
|**==**|Igualdad|Binary|
|**>**|Mayor que|Binary|
|**>=**|Mayor o igual que|Binary|
|**>>**|Desplazamiento a la derecha|Binary|
|**>>=**|Asignación y desplazamiento a la derecha|Binary|
|**[ ]**|Subíndice de matriz|—|
|**^**|OR exclusivo|Binary|
|**^=**|Asignación y OR exclusivo|Binary|
|**&#124;**|OR inclusivo bit a bit|Binary|
|**&#124;=**|Asignación y OR inclusivo bit a bit|Binary|
|**&#124;&#124;**|OR lógico|Binary|
|**~**|Complemento a uno|Unario|
|**delete**|Eliminar|—|
|**new**|Nuevo|—|
|operadores de conversión|operadores de conversión|Unario|

<sup>1</sup> incrementan las dos versiones de unario y operadores de decremento existen: preincremento y postincremento.

Consulte [reglas generales para la sobrecarga de operadores](../cpp/general-rules-for-operator-overloading.md) para obtener más información. En los temas siguientes se describen las restricciones de las distintas categorías de operadores sobrecargados:

- [Operadores unarios](../cpp/overloading-unary-operators.md)

- [Operadores binarios](../cpp/binary-operators.md)

- [Asignación](../cpp/assignment.md)

- [Llamada a función](../cpp/function-call-cpp.md)

- [Subíndices](../cpp/subscripting.md)

- [Acceso a miembros de clase](../cpp/member-access.md)

- [Incremento y decremento](../cpp/increment-and-decrement-operator-overloading-cpp.md).

- [Conversiones de tipos definidos por el usuario](../cpp/user-defined-type-conversions-cpp.md)

Los operadores que se muestran en la tabla siguiente no se pueden sobrecargar. La tabla incluye los símbolos de preprocesador **#** y **##**.

### <a name="nonredefinable-operators"></a>Operadores no redefinibles

|Operador|Name|
|-|-|
|**.**|Selección de miembro|
|**.&#42;**|Selección de puntero a miembro|
|**::**|Resolución de ámbito|
|**? :**|Condicional|
|**#**|Conversión de preprocesador en una cadena|
|**##**|Concatenación de preprocesadores|

Aunque el compilador suele llamar implícitamente a los operadores sobrecargados cuando se encuentran en el código, se pueden invocar explícitamente de la misma manera que cualquier función miembro o no miembro:

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente se sobrecarga la **+** operador para agregar dos números complejos y devuelve el resultado.

```cpp
// operator_overloading.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Complex {
   Complex( double r, double i ) : re(r), im(i) {}
   Complex operator+( Complex &other );
   void Display( ) {   cout << re << ", " << im << endl; }
private:
   double re, im;
};

// Operator overloaded using a member function
Complex Complex::operator+( Complex &other ) {
   return Complex( re + other.re, im + other.im );
}

int main() {
   Complex a = Complex( 1.2, 3.4 );
   Complex b = Complex( 5.6, 7.8 );
   Complex c = Complex( 0.0, 0.0 );

   c = a + b;
   c.Display();
}
```

```Output
6.8, 11.2
```

## <a name="in-this-section"></a>En esta sección

- [Reglas generales para la sobrecarga de operadores](../cpp/general-rules-for-operator-overloading.md)

- [Sobrecargar operadores unarios](../cpp/overloading-unary-operators.md)

- [Operadores binarios](../cpp/binary-operators.md)

- [Asignación](../cpp/assignment.md)

- [Llamada a función](../cpp/function-call-cpp.md)

- [Subíndices](../cpp/subscripting.md)

- [Acceso a miembros](../cpp/member-access.md)

## <a name="see-also"></a>Vea también

[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)