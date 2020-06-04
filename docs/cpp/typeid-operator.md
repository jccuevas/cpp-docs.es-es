---
title: typeid (Operador)
ms.date: 10/04/2019
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
ms.openlocfilehash: 93a2d3c494cd5aadafedcaaae9ec72809d633a4a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998751"
---
# <a name="typeid-operator"></a>typeid (Operador)

## <a name="syntax"></a>Sintaxis

```
typeid(type-id)
typeid(expression)
```

## <a name="remarks"></a>Comentarios

El operador **typeid** permite determinar el tipo de un objeto en tiempo de ejecución.

El resultado de **typeid** es un `const type_info&`. El valor es una referencia a un objeto `type_info` que representa el *identificador de tipo* o el tipo de la *expresión*, en función de la forma de **typeid** que se use. Para obtener más información, consulte [clase type_info](../cpp/type-info-class.md).

El operador **typeid** no funciona con tipos administrados (declaradores abstractos o instancias). Para obtener información sobre cómo obtener el <xref:System.Type> de un tipo especificado, vea [typeid](../extensions/typeid-cpp-component-extensions.md).

El operador **typeid** realiza una comprobación en tiempo de ejecución cuando se aplica a un valor l de un tipo de clase polimórfica, donde el tipo true del objeto no se puede determinar mediante la información estática proporcionada. Esos casos son:

- Una referencia a una clase

- Un puntero, desreferenciado con `*`

- Un puntero de subíndice (`[ ]`). (No es seguro usar un subíndice con un puntero a un tipo polimórfico).

Si la *expresión* apunta a un tipo de clase base, pero el objeto es realmente de un tipo derivado de esa clase base, es el resultado una referencia `type_info` para la clase derivada. La *expresión* debe apuntar a un tipo polimórfico (una clase con funciones virtuales). De lo contrario, el resultado es el `type_info` para la clase estática a la que se hace referencia en la *expresión*. Además, se debe desreferenciar el puntero para que el objeto utilizado sea el que señala. Sin desreferenciar el puntero, el resultado será el `type_info` para el puntero, no lo que señala. Por ejemplo:

```cpp
// expre_typeid_Operator.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <typeinfo>

class Base {
public:
   virtual void vvfunc() {}
};

class Derived : public Base {};

using namespace std;
int main() {
   Derived* pd = new Derived;
   Base* pb = pd;
   cout << typeid( pb ).name() << endl;   //prints "class Base *"
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"
   delete pd;
}
```

Si la *expresión* está desreferenciando un puntero y el valor de ese puntero es cero, **typeid** produce una [excepción bad_typeid](../cpp/bad-typeid-exception.md). Si el puntero no apunta a un objeto válido, se produce una excepción `__non_rtti_object`. Indica un intento de analizar la RTTI que desencadenó un error porque el objeto no es válido de algún modo. (Por ejemplo, es un puntero incorrecto o el código no se compiló con [/gr](../build/reference/gr-enable-run-time-type-information.md)).

Si la *expresión* no es un puntero, y no una referencia a una clase base del objeto, el resultado es una referencia `type_info` que representa el tipo estático de la *expresión*. El *tipo estático* de una expresión hace referencia al tipo de una expresión, ya que se conoce en tiempo de compilación. La semántica de ejecución se omite cuando se evalúa el tipo estático de una expresión. Además, las referencias se omiten cuando es posible al determinar el tipo estático de una expresión:

```cpp
// expre_typeid_Operator_2.cpp
#include <typeinfo>

int main()
{
   typeid(int) == typeid(int&); // evaluates to true
}
```

también se puede utilizar **typeid** en plantillas para determinar el tipo de un parámetro de plantilla:

```cpp
// expre_typeid_Operator_3.cpp
// compile with: /c
#include <typeinfo>
template < typename T >
T max( T arg1, T arg2 ) {
   cout << typeid( T ).name() << "s compared." << endl;
   return ( arg1 > arg2 ? arg1 : arg2 );
}
```

## <a name="see-also"></a>Vea también

[Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)\
[Palabras clave](../cpp/keywords-cpp.md)
