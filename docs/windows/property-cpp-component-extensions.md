---
title: propiedad (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- property_cpp
- property
dev_langs:
- C++
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b763131fe91e2df2385f2c06bcba8bc759d695a1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="property--c-component-extensions"></a>property (Extensiones de componentes de C++)
Declara un *propiedad*, que es una función miembro que se comporta y se accede como un miembro de datos o un elemento de matriz.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 Puede declarar uno de los siguientes tipos de propiedades.  
  
 *propiedad simple*  
 De forma predeterminada, crea un *descriptor de acceso set* que asigna el valor de propiedad, un *descriptor de acceso get* que recupera el valor de propiedad y un miembro de datos privado generado por el compilador que contiene el valor de propiedad.  
  
 *bloque de propiedad*  
 Se utiliza para crear descriptores de acceso definidos por el usuario get y/o set. La propiedad es de lectura y escritura si los dos descriptores de acceso get y set están definidos, de solo lectura si el descriptor de acceso get está definido, y de solo escritura si solo está definido el descriptor de acceso set.  
  
 Debe declarar explícitamente un miembro de datos que contenga el valor de propiedad.  
  
 *propiedad indizada*  
 Un bloque de propiedades que puede usar para obtener y establecer un valor de propiedad especificado por uno o más índices.  
  
 Puede crear una propiedad indizada que tenga un nombre de propiedad definido por el usuario o un *predeterminado* nombre de la propiedad. El nombre de una propiedad de índice predeterminado es el nombre de la clase en la que se define la propiedad. Para declarar una propiedad predeterminada, especifique la palabra clave `default` en lugar del nombre de propiedad.  
  
 Debe declarar explícitamente un miembro de datos que contenga el valor de propiedad. Para una propiedad indizada, el miembro de datos suele ser una matriz o una colección.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
property type property_name;

property type property_name { 
   access-modifier type get() inheritance-modifier {property_body}; 
   access-modifier void set(type value) inheritance-modifier {property_body};
} 

property type property_name[index_list] { 
   access-modifier type get(index_list) inheritance-modifier {property_body}; 
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
} 

property type default[index_list] { 
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}  
```  
  
### <a name="parameters"></a>Parámetros  
 `type`  
 El tipo de datos del valor de propiedad y, por consiguiente, la propiedad en sí.  
  
 `property_name`  
 Nombre de la propiedad.  
  
 `access-modifier`  
 Un calificador de acceso. Los calificadores válidos son `static` y `virtual`.  
  
 Los descriptores de acceso get o set no deben coincidir con el calificador `virtual`, pero sí con el calificador `static`.  
  
 `inheritance-modifier`  
 Un calificador de herencia. Los calificadores válidos son `abstract` y `sealed`.  
  
 `index_list`  
 Una lista delimitada por comas de uno o más índices. Cada índice consta de un tipo de índice y un identificador opcional que puede utilizarse en el cuerpo del método de propiedad.  
  
 `value`  
 El valor que se va a asignar a la propiedad en una operación set, o que se va a recuperar en una operación get.  
  
 `property_body`  
 El cuerpo del método de propiedad del descriptor de acceso set o get. `property_body` puede utilizar `index_list` para acceder al miembro de datos de propiedad subyacente, o como parámetros en el procesamiento definido por el usuario.  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 Para obtener más información, consulte [propiedades (C++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh755807.aspx).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Sintaxis**  
  
```cpp  
modifier property type property_name;

modifier property type property_name {
   modifier void set(type);
   modifier type get();
}
modifier property type property_name[index-list, value] {
   modifier void set(index-list, value);
   modifier type get(index-list);

modifier property type default[index];
}  
```  
  
 **Parámetros**  
  
 *Modificador*  
 Un modificador que se puede utilizar en la declaración de propiedad o en un método de descriptor de acceso get/set. Los valores posibles son `static` y `virtual`.  
  
 *type*  
 El tipo del valor representado por la propiedad.  
  
 *property_name*  
 Parámetros del método raise; debe coincidir con la firma del delegado.  
  
 *index_list*  
 Una lista delimitada por comas de uno o más índices especificados entre corchetes (el operador de subíndice, ([])). Para cada índice, especifique un tipo y, de forma opcional, un identificador que pueden utilizarse en el cuerpo del método de propiedad.  
  
 **Comentarios**  
  
 El primer ejemplo de sintaxis muestra un *propiedad simple*, que declara implícitamente un `set` y `get` método. El compilador crea automáticamente un campo privado para almacenar el valor de la propiedad.  
  
 El segundo ejemplo de sintaxis muestra un *el bloque de propiedad*, que declara explícitamente un `set` y `get` método.  
  
 El tercer ejemplo de sintaxis muestra definido por el cliente *index (propiedad)*. Una propiedad de índice toma parámetros además del valor que se debe establecer o recuperar. Debe especificar un nombre para la propiedad. A diferencia de una propiedad simple, los métodos `set` y/o `get` de una propiedad de índice deben definirse explícitamente, y se debe especificar un nombre para la propiedad.  
  
 El cuarto ejemplo de sintaxis muestra un *predeterminado* propiedad, que proporciona acceso de la matriz a una instancia del tipo. La palabra clave, `default`, solo sirve para especificar una propiedad predeterminada. El nombre de la propiedad predeterminada es el nombre del tipo en el que se define la propiedad.  
  
 La palabra clave `property` puede aparecer en una clase, interfaz o tipo de valor. Una propiedad puede tener una función get (solo lectura), una función set (solo escritura), o ambas (lectura y escritura).  
  
 El nombre de propiedad no puede coincidir con el nombre de la clase administrada que lo contiene. El tipo de valor devuelto de la función captadora debe coincidir con el tipo del último parámetro de una función establecedora correspondiente.  
  
 En cuanto al código de cliente, una propiedad tiene el aspecto de un miembro de datos normal, y puede escribirse en o leerse de con la misma sintaxis que un miembro de datos.  
  
 Los métodos get y set no deben coincidir con el modificador `virtual`.  
  
 La accesibilidad del método get puede ser diferente de la del método set.  
  
 La definición de un método de propiedad puede aparecer fuera del cuerpo de la clase, como en un método normal.  
  
 Lo métodos get y set para una propiedad deben coincidir con el **estático** modificador.  
  
 Una propiedad es escalar si sus métodos get y set se ajustan a la siguiente descripción:  
  
-   El método get no tiene parámetros y tiene el tipo de valor devuelto `T`.  
  
-   El método set tiene un parámetro de tipo `T`y el tipo devuelto **void**.  
  
 Debe haber solo una propiedad escalar declarada en un ámbito con el mismo identificador. Las propiedades escalares no se pueden sobrecargar.  
  
 Cuando se declara un miembro de datos de propiedad, el compilador inserta un miembro de datos (a veces denominado "memoria auxiliar") en la clase. Sin embargo, el nombre del miembro de datos está formado para que no pueda hacerse referencia al miembro en el origen como si fuera un miembro de datos reales de la clase contenedora. Use ildasm.exe para ver los metadatos para el tipo y ver el nombre generado por el compilador de la memoria auxiliar de la propiedad.  
  
 Se permite la accesibilidad diferente para los métodos del descriptor de acceso en un bloque de propiedades.  Es decir, el método set puede ser público y el método get puede ser privado.  Sin embargo, es un error que un método del descriptor de acceso tenga una accesibilidad menos restrictiva que la de la misma declaración de la propiedad.  
  
 `property` es una palabra clave contextual.  Para obtener más información, consulte [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se muestra la declaración y el uso de un miembro de datos de propiedad y un bloque de propiedades.  También se muestra que se puede definir un descriptor de acceso de propiedad fuera de la clase.  
  
```  
// mcppv2_property.cpp  
// compile with: /clr  
using namespace System;  
public ref class C {  
   int MyInt;  
public:  
  
   // property data member  
   property String ^ Simple_Property;  
  
   // property block  
   property int Property_Block {  
  
      int get();  
  
      void set(int value) {  
         MyInt = value;  
      }  
   }  
};  
  
int C::Property_Block::get() {  
   return MyInt;  
}  
  
int main() {  
   C ^ MyC = gcnew C();  
   MyC->Simple_Property = "test";  
   Console::WriteLine(MyC->Simple_Property);  
  
   MyC->Property_Block = 21;  
   Console::WriteLine(MyC->Property_Block);  
}  
```  
  
 **Salida**  
  
```Output  
test  
  
21  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)