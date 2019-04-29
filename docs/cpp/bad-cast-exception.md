---
title: bad_cast (Excepción)
ms.date: 11/04/2016
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 028fa8cc90b33aca6a37fb3b7f58b8c5fad81bd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284778"
---
# <a name="badcast-exception"></a>bad_cast (Excepción)

El **bad_cast** excepción la **dynamic_cast** operador como resultado de una conversión incorrecta a un tipo de referencia.

## <a name="syntax"></a>Sintaxis

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>Comentarios

La interfaz para **bad_cast** es:

```cpp
class bad_cast : public exception {
public:
   bad_cast(const char * _Message = "bad cast");
   bad_cast(const bad_cast &);
   virtual ~bad_cast();
};
```

El código siguiente contiene un ejemplo de un error **dynamic_cast** que produce el **bad_cast** excepción.

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo.h>
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

Se inicia una excepción porque el objeto que se convierte (una forma) no se deriva del tipo de conversión especificado (Circle). Para evitar la excepción, agregue estas declaraciones a `main`:

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

A continuación, invierta el sentido de la conversión en el **intente** bloquear como sigue:

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="see-also"></a>Vea también

[dynamic_cast (Operador)](../cpp/dynamic-cast-operator.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Control de excepciones de C++](../cpp/cpp-exception-handling.md)