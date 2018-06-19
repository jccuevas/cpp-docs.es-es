---
title: Información general sobre genéricos en Visual C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generics [C++], about generics
- default initializers [C++]
- type parameters [C++]
- constructed types
- type arguments [C++]
- constructed types, open [C++]
- open constructed types [C++]
- constructed types, closed [C++]
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19200e3c3c4ed67960905b697187dbb6b37a65e9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881008"
---
# <a name="overview-of-generics-in-visual-c"></a>Información general sobre genéricos en Visual C++
Los genéricos son tipos parametrizados compatibles con common language runtime. Un tipo con parámetros es un tipo que se define con un parámetro de tipo desconocido que se especifica cuando se utiliza la clase genérica.  
  
## <a name="why-generics"></a>¿Por qué genéricos?  
 C++ admite plantillas y las dos plantillas y tipos parametrizados para crear clases de colección con tipo de compatibilidad con elementos genéricos. Sin embargo, las plantillas proporcionan parametrización de tiempo de compilación. No se puede hacer referencia a un ensamblado que contiene una definición de plantilla y crear nuevas especializaciones de la plantilla. Una vez compilada, una plantilla especializada es similar a cualquier otra clase o método. En cambio, se emiten los genéricos en MSIL como un tipo parametrizado que se conoce en tiempo de ejecución como un tipo parametrizado; código fuente que hace referencia a un ensamblado que contiene un tipo genérico puede crear especializaciones de tipo genérico. Para obtener más información sobre la comparación de plantillas de Visual C++ y tipos genéricos, vea [genéricos y plantillas (Visual C++)](../windows/generics-and-templates-visual-cpp.md).  
  
## <a name="generic-functions-and-types"></a>Tipos y funciones genéricas  
 Tipos de clase, como son los tipos administrados, pueden ser genéricos. Un ejemplo de esto podría ser un `List` clase. El tipo de un objeto en la lista sería el parámetro de tipo. Si necesita un `List` clase para muchos tipos diferentes de objetos, antes de genéricos, es posible que haya usado un `List` que toma **System:: Object** como el tipo de elemento. Pero que permita a cualquier objeto (incluidos los objetos de un tipo incorrecto) que se usará en la lista. Esta lista se llama a una clase de colección sin tipo. En el mejor, puede comprobar el tipo en tiempo de ejecución y producir una excepción. O bien, es posible que haya usado una plantilla, que podría perder su calidad genérico una vez compilado en un ensamblado. Los consumidores del ensamblado no pudieron crear sus propios especializaciones de la plantilla. Los genéricos permiten crear clases de colección con tipo, digamos `List<int>` (lectura como "Lista de int") y `List<double>` ("lista de doble") no lo que generaría un error en tiempo de compilación si se intentó incluir un tipo de la colección diseñado para Aceptar en el tipo colección. Además, estos tipos permanecen genéricos después de que se compilen.  
  
 Una descripción de la sintaxis de las clases genéricas que puede encontrarse en [clases genéricas (C++ / CLI)](../windows/generic-classes-cpp-cli.md) `.` un nuevo espacio de nombres, <xref:System.Collections.Generic>, incluye un conjunto de tipos de colección con parámetros incluidos <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601>y <xref:System.Collections.Generic.LinkedList%601>.  
  
 Tanto instancia y las funciones miembro de clase estática, delegados y funciones globales también pueden ser genéricas. Funciones genéricas pueden ser necesarias si los parámetros de la función son de un tipo desconocido, o si la propia función debe trabajar con tipos genéricos. En muchos casos donde **System:: Object** puede haberse usado en el pasado como un parámetro para un tipo de objeto desconocido, un parámetro de tipo genérico puede utilizarse en su lugar, lo que permite más código con seguridad de tipos. Cualquier intento de pasar un tipo que la función no se diseñó para se marcará como un error en tiempo de compilación. Usar **System:: Object** como un parámetro de función, el paso accidental de un objeto que la función no se ha diseñado para tratar con no se detectan y se tendría que convertir el tipo de objeto desconocido a un tipo específico en el cuerpo de la función y cuenta con la posibilidad de una excepción InvalidCastException. Con un tipo genérico, el código intenta pasar un objeto a la función provocará un conflicto de tipos para que el cuerpo de la función se garantiza que el tipo correcto.  
  
 Las mismas ventajas que se aplican a las clases de colección basadas en genéricos. Clases de colección en el pasado utilizaría **System:: Object** para almacenar los elementos de una colección. Inserción de objetos de un tipo que la colección no se diseñó para no se ha marcado en tiempo de compilación y a menudo ni siquiera cuando se insertaron los objetos. Normalmente, un objeto podría convertirse a algún otro tipo al que se tuvo acceso en la colección. Solo cuando la conversión no se pudo sería el tipo inesperado detectado. Genéricos soluciona este problema en tiempo de compilación mediante la detección de cualquier código que inserta un tipo que no coincide con (o convertir implícitamente a) el parámetro de tipo de la colección genérica.  
  
 Para obtener una descripción de la sintaxis, vea [funciones genéricas (C++ / CLI)](../windows/generic-functions-cpp-cli.md).  
  
## <a name="terminology-used-with-generics"></a>Terminología que se usa con los genéricos  
  
##### <a name="type-parameters"></a>Parámetros de tipo  
 Una declaración genérica contiene uno o más tipos desconocidos denominados *parámetros de tipo*. Parámetros de tipo tienen un nombre que representa el tipo dentro del cuerpo de la declaración genérica. El parámetro de tipo se utiliza como un tipo dentro del cuerpo de la declaración genérica. La declaración genérica para lista < T\> contiene el parámetro de tipo T.  
  
##### <a name="type-arguments"></a>Argumentos de tipo  
 El *el argumento de tipo* es el tipo real utilizado en lugar del parámetro de tipo cuando genérico está diseñado para un tipo específico o tipos. Por ejemplo, `int` es el argumento de tipo en `List<int>`. Tipos de valor y tipos de identificador son los únicos tipos que se permiten en como un argumento de tipo genérico.  
  
##### <a name="constructed-type"></a>Tipo construido  
 Un tipo construido a partir de un tipo genérico se conoce como un *tipo construido*. Un tipo completamente especificado, como `List<T>` es un *tipo construido abierto*; un tipo completo especificado, como `List<double>,` es un *tipo construido cerrado* o *especializada de tipo* . Tipos construidos abiertos pueden utilizarse en la definición de otros métodos ni tipos genéricos y pueden no estar totalmente especificados hasta que los incluye genérica es en sí misma especificado. Por ejemplo, el siguiente es un uso de un tipo construido abierto como una clase base para un tipo genérico:  
  
 `// generics_overview.cpp`  
  
 `// compile with: /clr /c`  
  
 `generic <typename T>`  
  
 `ref class List {};`  
  
 `generic <typename T>`  
  
 `ref class Queue : public List<T> {};`  
  
##### <a name="constraint"></a>Restricción  
 Una restricción es una restricción en los tipos que puede utilizarse como un parámetro de tipo. Por ejemplo, una clase genérica determinada podría aceptar sólo las clases que heredan de una clase especificada o implementar una interfaz especificada. Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="reference-types-and-value-types"></a>Tipos de referencia y tipos de valor  
 Controla los tipos y tipos de valor pueden utilizarse como argumentos de tipo. En la definición genérica, en el que pueden usar cualquiera de estos tipos, la sintaxis es los tipos de referencia. Por ejemplo, el **->** operador se usa para tener acceso a los miembros del tipo del parámetro de tipo si el tipo que se utilizan en el futuro es un tipo de referencia o un tipo de valor o no. Cuando se utiliza un tipo de valor como argumento de tipo, el tiempo de ejecución genera el código que usa los tipos de valor directamente, sin conversión boxing de los tipos de valor.  
  
 Cuando se usa un tipo de referencia como un argumento de tipo genérico, use la sintaxis de identificador. Cuando se usa un tipo de valor como un argumento de tipo genérico, use el nombre del tipo directamente.  
  
 `// generics_overview_2.cpp`  
  
 `// compile with: /clr`  
  
 `generic <typename T>`  
  
 `ref class GenericType {};`  
  
 `ref class ReferenceType {};`  
  
 `value struct ValueType {};`  
  
 `int main() {`  
  
 `GenericType<ReferenceType^> x;`  
  
 `GenericType<ValueType> y;`  
  
 `}`  
  
## <a name="type-parameters"></a>Parámetros de tipo  
 Parámetros de tipo en una clase genérica se tratan como otros identificadores. Sin embargo, dado que no se conoce el tipo, hay restricciones sobre su uso. Por ejemplo, no puede usar los miembros y métodos de la clase de parámetro de tipo a menos que el parámetro de tipo se sabe que admite a estos miembros. Es decir, para tener acceso a un miembro a través del parámetro de tipo, debe agregar el tipo que contiene al miembro a la lista de restricciones del parámetro de tipo.  
  
 `// generics_overview_3.cpp`  
  
 `// compile with: /clr`  
  
```  
interface class I {  
   void f1();  
   void f2();  
};  
  
ref struct R : public I {  
   virtual void f1() {}  
   virtual void f2() {}   
   virtual void f3() {}   
};  
  
generic <typename T>  
where T : I  
void f(T t) {  
   t->f1();  
   t->f2();  
   safe_cast<R^>(t)->f3();  
}  
  
int main() {  
   f(gcnew R());  
}  
```  
  
 Estas restricciones se aplican a los operadores así. No puede usar un parámetro de tipo genérico sin restricciones el `==` y `!=` operadores para comparar dos instancias del parámetro de tipo, en caso de que el tipo no admite estos operadores. Estas comprobaciones son necesarias para los tipos genéricos, pero no para las plantillas, porque se pueden especializar genéricos en tiempo de ejecución con cualquier clase que satisface las restricciones, cuando es demasiado tarde para comprobar el uso de miembros no válidos.  
  
 Una instancia predeterminada del parámetro de tipo puede crearse mediante el `()` operador. Por ejemplo:  
  
 `T t = T();`  
  
 donde `T` es un parámetro de tipo en una definición de clase o método genérico, inicializa la variable en su valor predeterminado. Si `T` es una clase ref será un puntero nulo; si `T` es una clase de valor, el objeto se inicializa en cero. Esto se denomina una *predeterminado inicializador*.  
  
## <a name="see-also"></a>Vea también  
 [Genéricos](../windows/generics-cpp-component-extensions.md)