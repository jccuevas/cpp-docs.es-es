---
title: "Informaci&#243;n general sobre gen&#233;ricos en Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipos construidos"
  - "tipos construidos, cerrado [C++]"
  - "tipos construidos, abrir [C++]"
  - "inicializadores predeterminados [C++]"
  - "genéricos [C++], acerca de los genéricos"
  - "tipos construidos abiertos [C++]"
  - "argumentos de tipo [C++]"
  - "parámetros de tipo [C++]"
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n general sobre gen&#233;ricos en Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los genéricos son tipos con parámetros compatibles con Common Language Runtime.  Tipo parametrizado es un tipo definido con un parámetro de tipo desconocido se especifica que cuando se utiliza el genérico.  
  
## ¿Por qué genéricos?  
 C\+\+ admite las plantillas y las plantillas y los tipos parametrizados compatibilidad de genéricos crear clases de colección con tipo.  Sin embargo, las plantillas proporcionan la parametrización en tiempo de compilación.  No puede hacer referencia a un ensamblado que contiene una definición de plantilla y crear nuevas especializaciones de la plantilla.  Una vez que se compila, una plantilla especializada es cualquier otra clase o método.  En cambio, los genéricos se emiten en MSIL como tipo parametrizado conocido por el runtime para ser un tipo parametrizado; el código fuente que hace referencia a un ensamblado que contenga un tipo genérico puede crear especializaciones de tipo genérico.  Para obtener más información sobre la comparación de las plantillas y los genéricos de Visual C\+\+, vea [Genéricos y plantillas \(Visual C\+\+\)](../windows/generics-and-templates-visual-cpp.md).  
  
## Funciones y tipos genéricos  
 Los tipos de clase, como son tipos administrados, pueden ser genéricos.  Un ejemplo podría ser una clase de `List` .  El tipo de un objeto de la lista sería el parámetro de tipo.  Si se necesitó una clase de `List` para diferentes tipos de objetos, antes de que los genéricos se pueden haber utilizado `List` que toma **System::Object** como tipo de elemento.  Pero eso permitiría que los objetos \(incluidos de tipo incorrecto\) fuera utilizado en la lista.  Esta lista se denominaría una clase de colección sin tipo.  En el mejor de los casos, puede comprobar el tipo en tiempo de ejecución y producir una excepción.  O bien, puede que haya utilizado una plantilla, que pierde su calidad genérica compilada una vez en un ensamblado.  Los consumidores del ensamblado no pueden crear sus propias especializaciones de la plantilla.  Los genéricos permiten crear clases de colección con tipo, de modo `List<int>` \(lectura como “lista de int”\) y `List<double>` \(“lista de doble”\) que generarían un error en tiempo de compilación si ha intentado colocar un tipo que la colección no está diseñada para aceptar en la colección con tipo.  Además, estos tipos permanecen genéricos después de que se compilen.  
  
 Una descripción de la sintaxis de clases genéricas se puede encontrar en el nuevo espacio de nombres de [Clases genéricas \(C\+\+\/CLI\)](../Topic/Generic%20Classes%20\(C++-CLI\).md)`.` A, <xref:System.Collections.Generic>, introduce un conjunto de tipos de colección con parámetros incluidos <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601> y <xref:System.Collections.Generic.LinkedList%601>.  Para obtener más información, vea [Tipos genéricos en la biblioteca de clases de .NET Framework](../Topic/Generics%20in%20the%20.NET%20Framework%20Class%20Library%20\(C%23%20Programming%20Guide\).md).  
  
 La instancia y las funciones miembro estáticas de clase, delegados, y las funciones globales pueden ser genéricos.  Las funciones genéricas pueden ser necesarias si los parámetros de la función son de un tipo desconocido, o si la propia función debe trabajar con los tipos genéricos.  En muchos casos donde **System::Object** puede haberse utilizado en el pasado como un parámetro para un tipo de objeto desconocido, un parámetro de tipo genérico se puede utilizar en su lugar, teniendo en cuenta un código tipo\- más seguro.  Cualquier intento de pasar un tipo que la función no está diseñada para se marca como un error en tiempo de compilación.  Mediante **System::Object** como parámetro de la función, el paso inadvertido de un objeto de que la función no debía tratar no sería detectado, y tendría que convertir el tipo de objeto desconocido para un tipo específico en el cuerpo de la función, y explica la posibilidad de InvalidCastException.  Con un genérico, el código que intenta pasar un objeto a la función provocaría un conflicto de tipo para que el cuerpo de la función se garantiza para obtener el tipo correcto.  
  
 Las ventajas se aplican a las clases de colección compiladas en genéricos.  Las clases de colección del último utilizarían **System::Object** para almacenar elementos en una colección.  La inserción de objetos de un tipo que la colección no está diseñada para no se marca\/marcada en tiempo de compilación y, a menudo ni siquiera cuando los objetos se insertarán.  Normalmente, un objeto se echado a otro tipo cuando se obtiene de la colección.  Cuando se produce un error en la conversión detectarían el tipo inesperado.  Los genéricos solucionan este problema en tiempo de compilación detectar cualquier código que inserte un tipo que no coincida con \(o convertir implícitamente\) el parámetro de tipo de colección genérica.  
  
 Para obtener una descripción de la sintaxis, vea [Funciones genéricas \(C\+\+\/CLI\)](../windows/generic-functions-cpp-cli.md).  
  
## Terminología utilizada con genéricos  
  
##### Parámetros de tipo  
 Una declaración genérica contiene uno o más tipos desconocidos conocidos como *parámetros de tipo*.  Los parámetros de tipo se les da un nombre que representa el tipo en el cuerpo de la declaración genérica.  El parámetro de tipo se utiliza como un tipo en el cuerpo de la declaración genérica.  La declaración genérica para List\<T\> contiene el parámetro de tipo t.  
  
##### Argumentos de tipo  
 *El argumento de tipo* es el tipo real utilizado en lugar del parámetro de tipo cuando el genérico está especializado para un tipo específico o los tipos.  Por ejemplo, `int` es el argumento de tipo en `List<int>`.  Los tipos de valor y tipos ID son los únicos tipos permitidos en como argumento de tipo genérico.  
  
##### Tipo construido  
 Hacen referencia a un tipo construido a partir de un tipo genérico como *tipo construido*.  Un tipo especificado no completamente, por ejemplo `List<T>` es un *tipo construido abierto*; un tipo especificado completamente, por ejemplo `List<double>,` es un *tipo construido cerrado* o *tipo especializado*.  Los tipos construidos Abrir pueden utilizarse en la definición de otros tipos o métodos genéricos y no pueden especificar totalmente hasta que el agregar genérico en sí se especifique.  Por ejemplo, lo siguiente es un uso de un tipo construido abiertas como clase base para un genérico:  
  
 `// generics_overview.cpp`  
  
 `// compile with: /clr /c`  
  
 `generic <typename T>`  
  
 `ref class List {};`  
  
 `generic <typename T>`  
  
 `ref class Queue : public List<T> {};`  
  
##### Restricción  
 Una restricción es una restricción en los tipos que se pueden utilizar como parámetro de tipo.  Por ejemplo, una clase genérica especificada podría aceptar únicamente las clases que heredan de la clase especificada, o implementa una interfaz especificada.  Para obtener más información, vea [Restricciones de parámetros de tipo genérico \(C\+\+\/CLI\)](../Topic/Constraints%20on%20Generic%20Type%20Parameters%20\(C++-CLI\).md).  
  
## Tipos de referencia y tipos de valor  
 Los tipos y los tipos de valor de los identificadores pueden utilizar como argumentos de tipo.  En la definición genérica, en la que el que se puede utilizar, la sintaxis es la de tipos de referencia.  Por ejemplo, se utiliza el operador de **\-\>** para tener acceso a los miembros del tipo del parámetro de tipo si el tipo utilizado finalmente es un tipo de referencia o un tipo de valor.  Cuando se utiliza un tipo de valor como el argumento de tipo, el tiempo de ejecución genera el código que utiliza los tipos de valor directamente sin la conversión de los tipos de valor.  
  
 Al utilizar un tipo de referencia como argumento de tipo genérico, utilice la sintaxis de identificador.  Al utilizar un tipo de valor como argumento de tipo genérico, utilice el nombre del tipo directamente.  
  
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
  
## Parámetros de tipo  
 Los parámetros de tipo en una clase genérica se tratan como otros identificadores.  Sin embargo, dado que no se conoce el tipo, hay restricciones en el uso.  Por ejemplo, no puede usar los miembros y métodos de la clase de parámetros de tipo a menos que el parámetro de tipo se conoce para admitir estos miembros.  Es decir, para tener acceso a un miembro con el parámetro de tipo, debe agregar el tipo que contiene el miembro a la lista de restricciones del parámetro de tipo.  
  
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
  
 Estas restricciones se aplican a los operadores también.  Un parámetro de tipo genérico libre no puede usar los operadores de `==` y de `!=` para comparar dos instancias del parámetro de tipo, en caso de que el tipo no admite estos operadores.  Estas comprobaciones son necesarias para genéricos, pero no para plantillas, porque los genéricos pueden especializar en tiempo de ejecución con cualquier tipo que satisfaga las restricciones, cuando es demasiado hacia atrás comprobar para el uso de miembros no válidos.  
  
 Una instancia predeterminada del parámetro de tipo se pueden crear mediante el operador de `()` .  Por ejemplo:  
  
 `T t = T();`  
  
 donde es un parámetro de tipo `T` en una definición genérica de la clase o método, inicializa la variable a su valor predeterminado.  Si `T` es una clase de referencia se puntero null; si `T` es una clase de valor, el objeto se inicializa en cero.  Esto se denomina un *inicializador predeterminado*.  
  
## Vea también  
 [Genéricos](../windows/generics-cpp-component-extensions.md)