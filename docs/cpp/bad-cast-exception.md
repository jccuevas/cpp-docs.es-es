---
title: bad_cast (Excepción)
ms.date: 10/04/2019
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 7384394fb53c6aa4bc009a903ba0ed22bf0ed0d6
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998775"
---
# <a name="bad_cast-exception"></a>bad_cast (Excepción)

El operador **dynamic_cast** produce la excepción **bad_cast** como resultado de una conversión errónea en un tipo de referencia.

## <a name="syntax"></a>Sintaxis

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>Comentarios

La interfaz para **bad_cast** es:

```cpp
class bad_cast : public exception
```

El código siguiente contiene un ejemplo de un **dynamic_cast** erróneo que produce la excepción **bad_cast** .

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo>
#include <iostream>

class Shape {
public:
   virtual void virtualfunc() const {}
};

class Circle: public Shape {
public:
   virtual void virtualfunc() const {}
};

using namespace std;
int main() {
   Shape shape_instance;
   Shape& ref_shape = shape_instance;
   try {
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);
   }
   catch (bad_cast b) {
      cout << "Caught: " << b.what();
   }
}
```

La excepción se produce porque el objeto que se va a convertir (una forma) no se deriva del tipo de conversión especificado (círculo). Para evitar la excepción, agregue estas declaraciones a `main`:

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

A continuación, invierta el sentido de la conversión en el bloque **try** de la siguiente manera:

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[bad_cast](#bad_cast)|Constructor para los objetos de tipo `bad_cast`.|

### <a name="functions"></a>Funciones

|Función|Descripción|
|-|-|
|[what](#what)|TBD|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator=](#op_eq)|Operador de asignación que asigna un objeto `bad_cast` a otro.|

## <a name="bad_cast"></a>bad_cast

Constructor para los objetos de tipo `bad_cast`.

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a> operator=

Operador de asignación que asigna un objeto `bad_cast` a otro.

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a>elemento

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>Vea también

[dynamic_cast (operador](../cpp/dynamic-cast-operator.md)) \
[Palabras clave](../cpp/keywords-cpp.md)\
[Control de excepciones de C++](../cpp/cpp-exception-handling.md)
