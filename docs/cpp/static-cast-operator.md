---
title: static_cast (Operador)
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: 37708bf50b28eb120af8e8a79e770c3121e6f509
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178592"
---
# <a name="static_cast-operator"></a>static_cast (Operador)

Convierte una *expresión* al tipo de identificador de *tipo,* basándose solo en los tipos que se encuentran en la expresión.

## <a name="syntax"></a>Sintaxis

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>Observaciones

En Standard C++, no se realiza ninguna comprobación de tipo en tiempo de ejecución como ayuda para garantizar la seguridad de la conversión. En C++/CX, se realiza una comprobación en tiempo de compilación y en tiempo de ejecución. Para obtener más información, consulta [Conversión](casting.md).

El operador **static_cast** se puede utilizar para operaciones como la conversión de un puntero a una clase base en un puntero a una clase derivada. Estas conversiones no siempre son seguras.

En general, se usa **static_cast** cuando se desea convertir tipos de datos numéricos, como enumeraciones, en valores int o ints en valores Float, y está seguro de los tipos de datos implicados en la conversión. **static_cast** conversiones no son tan seguras como **dynamic_cast** conversiones, porque **static_cast** no realiza ninguna comprobación de tipo en tiempo de ejecución, mientras que la **dynamic_cast** sí lo hace. Un **dynamic_cast** a un puntero ambiguo producirá un error, mientras que un **static_cast** devuelve como si no hubiese ningún problema; Esto puede ser peligroso. Aunque **dynamic_cast** conversiones son más seguras, **dynamic_cast** solo funciona en punteros o referencias, y la comprobación de tipo en tiempo de ejecución es una sobrecarga. Para obtener más información, vea [operador dynamic_cast](../cpp/dynamic-cast-operator.md).

En el ejemplo siguiente, la línea `D* pd2 = static_cast<D*>(pb);` no es segura porque `D` puede tener campos y métodos que no están en `B`. Sin embargo, la línea `B* pb2 = static_cast<B*>(pd);` es una conversión segura porque `D` siempre contiene todo `B`.

```cpp
// static_cast_Operator.cpp
// compile with: /LD
class B {};

class D : public B {};

void f(B* pb, D* pd) {
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields
                                   // and methods that are not in B.

   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always
                                   // contains all of B.
}
```

A diferencia de [dynamic_cast](../cpp/dynamic-cast-operator.md), no se realiza ninguna comprobación en tiempo de ejecución en la conversión **static_cast** de `pb`. El objeto al que apunta `pb` puede no ser un objeto de tipo `D`, en cuyo caso el uso de `*pd2` podría ser desastroso. Por ejemplo, la llamada a una función que es miembro de la clase `D`, pero no de la clase `B`, podría producir una infracción de acceso.

Los operadores **dynamic_cast** y **static_cast** mueven un puntero a lo largo de una jerarquía de clases. Sin embargo, **static_cast** se basa exclusivamente en la información proporcionada en la instrucción CAST y, por tanto, no es segura. Por ejemplo:

```cpp
// static_cast_Operator_2.cpp
// compile with: /LD /GR
class B {
public:
   virtual void Test(){}
};
class D : public B {};

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);
   D* pd2 = static_cast<D*>(pb);
}
```

Si `pb` apunta realmente un objeto de tipo `D`, `pd1` y `pd2` obtienen el mismo valor. También obtienen el mismo valor si `pb == 0`.

Si `pb` apunta a un objeto de tipo `B` y no a la clase `D` completa, **dynamic_cast** sabrá lo suficiente como para devolver cero. Sin embargo, **static_cast** se basa en la aserción del programador que `pb` apunta a un objeto de tipo `D` y simplemente devuelve un puntero a que supone `D` objeto.

Por consiguiente, **static_cast** puede hacer lo contrario de las conversiones implícitas, en cuyo caso los resultados son indefinidos. Se deja al programador comprobar que los resultados de una conversión **static_cast** son seguros.

Este comportamiento también se aplica a los tipos distintos de los tipos de clase. Por ejemplo, **static_cast** se puede utilizar para convertir de un tipo int a un valor **Char**. Sin embargo, es posible que el **carácter** resultante no tenga suficientes bits para contener todo el valor **int** . Una vez más, se deja al programador comprobar que los resultados de una conversión **static_cast** son seguros.

El operador **static_cast** también se puede utilizar para realizar cualquier conversión implícita, incluidas las conversiones estándar y las conversiones definidas por el usuario. Por ejemplo:

```cpp
// static_cast_Operator_3.cpp
// compile with: /LD /GR
typedef unsigned char BYTE;

void f() {
   char ch;
   int i = 65;
   float f = 2.5;
   double dbl;

   ch = static_cast<char>(i);   // int to char
   dbl = static_cast<double>(f);   // float to double
   i = static_cast<BYTE>(ch);
}
```

El operador **static_cast** puede convertir explícitamente un valor entero en un tipo de enumeración. Si el valor del tipo entero no está dentro del intervalo de valores de enumeración, el valor de enumeración resultante no está definido.

El operador **static_cast** convierte un valor de puntero nulo en el valor de puntero nulo del tipo de destino.

Cualquier expresión se puede convertir explícitamente al tipo void por el operador **static_cast** . El tipo void de destino puede incluir opcionalmente el atributo **const**, **volatile**o **__unaligned** .

El operador **static_cast** no puede desechar los atributos **const**, **volatile**o **__unaligned** . Consulte [Const_cast operador](../cpp/const-cast-operator.md) para obtener información sobre cómo quitar estos atributos.

**C++/CLI:** Debido al riesgo de realizar conversiones no comprobadas sobre un recolector de elementos no utilizados de reubicación, el uso de **static_cast** solo debe estar en código crítico para el rendimiento cuando esté seguro de que funcionará correctamente. Si debe usar **static_cast** en modo de versión, sustitúyalo por [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) en las compilaciones de depuración para asegurarse de que se ha realizado correctamente.

## <a name="see-also"></a>Consulte también

[Operadores de conversión](../cpp/casting-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
