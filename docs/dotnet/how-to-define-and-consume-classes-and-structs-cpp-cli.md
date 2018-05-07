---
title: 'Cómo: definir y utilizar clases y Structs (C++ / CLI) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d8356d96b0193566814c0d52173a03a3a79d08d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>Cómo: Definir y utilizar clases y structs (C++/CLI)
Este artículo muestra cómo definir y utilizar tipos de referencia definidos por el usuario y tipos de valor en C++ / CLI.  
  
##  <a name="BKMK_Contents"></a> Contenido  
 [Creación de instancias de objeto](#BKMK_Object_instantiation)  
  
 [Clases abstractas implícitamente](#BKMK_Implicitly_abstract_classes)  
  
 [Visibilidad de tipos](#BKMK_Type_visibility)  
  
 [Visibilidad de miembros](#BKMK_Member_visibility)  
  
 [Clases nativas públicas y privadas](#BKMK_Public_and_private_native_classes)  
  
 [Constructores estáticos](#BKMK_Static_constructors)  
  
 [Semántica de este puntero](#BKMK_Semantics_of_the_this_pointer)  
  
 [Funciones de ocultación por signatura](#BKMK_Hide_by_signature_functions)  
  
 [Constructores de copias](#BKMK_Copy_constructors)  
  
 [Destructores y finalizadores](#BKMK_Destructors_and_finalizers)  
  
##  <a name="BKMK_Object_instantiation"></a> Creación de instancias de objeto  
 Solo se pueden crear instancias de los tipos de valor y de referencia (ref) en el montón administrado, no en la pila o en el montón nativo.  
  
```  
// mcppv2_ref_class2.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   int i;  
  
   // nested class  
   ref class MyClass2 {  
   public:  
      int i;  
   };  
  
   // nested interface  
   interface struct MyInterface {  
      void f();  
   };  
};  
  
ref class MyClass2 : public MyClass::MyInterface {  
public:  
   virtual void f() {  
      System::Console::WriteLine("test");  
   }  
};  
  
public value struct MyStruct {  
   void f() {  
      System::Console::WriteLine("test");  
   }     
};  
  
int main() {  
   // instantiate ref type on garbage-collected heap  
   MyClass ^ p_MyClass = gcnew MyClass;  
   p_MyClass -> i = 4;  
  
   // instantiate value type on garbage-collected heap  
   MyStruct ^ p_MyStruct = gcnew MyStruct;  
   p_MyStruct -> f();  
  
   // instantiate value type on the stack  
   MyStruct p_MyStruct2;  
   p_MyStruct2.f();  
  
   // instantiate nested ref type on garbage-collected heap  
   MyClass::MyClass2 ^ p_MyClass2 = gcnew MyClass::MyClass2;  
   p_MyClass2 -> i = 5;  
}  
```  
  
##  <a name="BKMK_Implicitly_abstract_classes"></a> Clases abstractas implícitamente  
 Un *clase implícitamente abstracta* no se pueden crear instancias. Una clase es implícitamente abstracta si el tipo base de la clase es una interfaz y la clase no implementa todas las funciones miembro de la interfaz.  
  
 Si no puede construir objetos de una clase que se derive de una interfaz, el motivo puede ser que la clase es implícitamente abstracta. Para obtener más información sobre las clases abstractas, vea [abstracta](../windows/abstract-cpp-component-extensions.md).  
  
 El ejemplo de código siguiente muestra que no se pueden crear instancias de la clase `MyClass` porque la función `MyClass::func2` no se implementa. Para permitir que el ejemplo se compile, quite el comentario `MyClass::func2`.  
  
```  
// mcppv2_ref_class5.cpp  
// compile with: /clr  
interface struct MyInterface {  
   void func1();  
   void func2();  
};  
  
ref class MyClass : public MyInterface {  
public:  
   void func1(){}  
   // void func2(){}  
};  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;   // C2259   
                                          // To resolve, uncomment MyClass::func2.  
}  
```  
  
##  <a name="BKMK_Type_visibility"></a> Visibilidad de tipos  
 Puede controlar la visibilidad de los tipos de Common Language Runtime (CLR) de modo que, si se hace referencia a un ensamblado, los tipos del ensamblado puedan ser visibles o no visibles fuera del ensamblado.  
  
 `public` indica que un tipo es visible para cualquier archivo de código fuente que contiene un `#using` la directiva para el ensamblado que contiene el tipo.  `private` indica que un tipo no es visible para los archivos de código fuente que contienen un `#using` la directiva para el ensamblado que contiene el tipo. Sin embargo, los tipos privados son visibles dentro del mismo ensamblado. De forma predeterminada, la visibilidad de una clase es `private`.  
  
 De forma predeterminada antes de Visual C++ 2005, los tipos nativos tenían accesibilidad pública fuera del ensamblado. Habilitar [advertencia del compilador (nivel 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) para ayudarle a ver dónde se utilizan los tipos nativos privados incorrectamente. Use la [make_public](../preprocessor/make-public.md) pragma para dar accesibilidad pública a un tipo nativo en un archivo de código fuente que no se puede modificar.  
  
 Para obtener más información, consulte [#using (directiva)](../preprocessor/hash-using-directive-cpp.md).  
  
 El ejemplo siguiente muestra cómo declarar tipos y especificar su accesibilidad, y después tiene acceso a esos tipos en el ensamblado. Por supuesto, si se hace referencia a un ensamblado que tiene tipos privados mediante `#using`, solo son visibles los tipos públicos del ensamblado.  
  
```  
// type_visibility.cpp  
// compile with: /clr  
using namespace System;  
// public type, visible inside and outside assembly  
public ref struct Public_Class {  
   void Test(){Console::WriteLine("in Public_Class");}  
};  
  
// private type, visible inside but not outside assembly  
private ref struct Private_Class {  
   void Test(){Console::WriteLine("in Private_Class");}  
};  
  
// default accessibility is private  
ref class Private_Class_2 {  
public:  
   void Test(){Console::WriteLine("in Private_Class_2");}  
};  
  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   a->Test();  
  
   Private_Class ^ b = gcnew Private_Class;  
   b->Test();  
  
   Private_Class_2 ^ c = gcnew Private_Class_2;  
   c->Test();  
}  
```  
  
 **Salida**  
  
```Output  
in Public_Class  
in Private_Class  
in Private_Class_2  
```  
  
 Ahora, escribamos de nuevo el ejemplo anterior para generarlo como archivo DLL.  
  
```  
// type_visibility_2.cpp  
// compile with: /clr /LD  
using namespace System;  
// public type, visible inside and outside the assembly  
public ref struct Public_Class {  
   void Test(){Console::WriteLine("in Public_Class");}  
};  
  
// private type, visible inside but not outside the assembly  
private ref struct Private_Class {  
   void Test(){Console::WriteLine("in Private_Class");}  
};  
  
// by default, accessibility is private  
ref class Private_Class_2 {  
public:  
   void Test(){Console::WriteLine("in Private_Class_2");}  
};  
```  
  
 El ejemplo siguiente muestra cómo obtener acceso a tipos fuera del ensamblado. En este ejemplo, el cliente utiliza el componente que se compila en el ejemplo anterior.  
  
```  
// type_visibility_3.cpp  
// compile with: /clr  
#using "type_visibility_2.dll"  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   a->Test();  
  
   // private types not accessible outside the assembly  
   // Private_Class ^ b = gcnew Private_Class;  
   // Private_Class_2 ^ c = gcnew Private_Class_2;  
}  
```  
  
 **Salida**  
  
```Output  
in Public_Class  
```  
  
##  <a name="BKMK_Member_visibility"></a> Visibilidad de miembros  
 Puede hacer que el acceso a un miembro de una clase pública dentro del mismo ensamblado sea diferente del acceso a él desde fuera del ensamblado mediante pares de los especificadores de acceso `public`, `protected` y `private`.  
  
 En esta tabla se resume el efecto de los distintos especificadores de acceso:  
  
|Especificador|Efecto|  
|---------------|------------|  
|public|El miembro es accesible dentro y fuera del ensamblado.  Vea [público](../cpp/public-cpp.md) para obtener más información.|  
|private|El miembro no es accesible, ni dentro ni fuera del ensamblado.  Vea [privada](../cpp/private-cpp.md) para obtener más información.|  
|protected|El miembro es accesible dentro y fuera del ensamblado, pero solo para los tipos derivados.  Vea [protegido](../cpp/protected-cpp.md) para obtener más información.|  
|internal|Miembro es público dentro del ensamblado, pero es privado fuera del ensamblado.  `internal` es una palabra clave contextual.  Para obtener más información, consulte [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).|  
|público protegido - o - protegido pública|El miembro es público dentro del ensamblado, pero está protegido fuera del ensamblado.|  
|privado protegido - o - protegido privada|El miembro está protegido dentro del ensamblado, pero es privado fuera del ensamblado.|  
  
 El ejemplo siguiente muestra un tipo público cuyos miembros se han declarado con distintas accesibilidades y, a continuación, muestra el acceso de esos miembros desde dentro del ensamblado.  
  
```  
  
// compile with: /clr  
using namespace System;  
// public type, visible inside and outside the assembly  
public ref class Public_Class {  
public:  
   void Public_Function(){System::Console::WriteLine("in Public_Function");}  
  
private:  
   void Private_Function(){System::Console::WriteLine("in Private_Function");}  
  
protected:  
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}  
  
internal:  
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}  
  
protected public:  
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}  
  
public protected:  
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}  
  
private protected:  
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}  
  
protected private:  
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}  
};  
  
// a derived type, calls protected functions  
ref struct MyClass : public Public_Class {  
   void Test() {  
      Console::WriteLine("=======================");  
      Console::WriteLine("in function of derived class");  
      Protected_Function();  
      Protected_Private_Function();  
      Private_Protected_Function();  
      Console::WriteLine("exiting function of derived class");  
      Console::WriteLine("=======================");  
   }  
};  
  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   MyClass ^ b = gcnew MyClass;  
   a->Public_Function();  
   a->Protected_Public_Function();  
   a->Public_Protected_Function();  
  
   // accessible inside but not outside the assembly  
   a->Internal_Function();  
  
   // call protected functions  
   b->Test();  
  
   // not accessible inside or outside the assembly  
   // a->Private_Function();  
}  
```  
  
 **Salida**  
  
```Output  
in Public_Function  
in Protected_Public_Function  
in Public_Protected_Function  
in Internal_Function  
=======================  
in function of derived class  
in Protected_Function  
in Protected_Private_Function  
in Private_Protected_Function  
exiting function of derived class  
=======================  
```  
  
 Ahora compilemos el ejemplo anterior como un archivo DLL.  
  
```  
  
// compile with: /clr /LD  
using namespace System;  
// public type, visible inside and outside the assembly  
public ref class Public_Class {  
public:  
   void Public_Function(){System::Console::WriteLine("in Public_Function");}  
  
private:  
   void Private_Function(){System::Console::WriteLine("in Private_Function");}  
  
protected:  
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}  
  
internal:  
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}  
  
protected public:  
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}  
  
public protected:  
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}  
  
private protected:  
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}  
  
protected private:  
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}  
};  
  
// a derived type, calls protected functions  
ref struct MyClass : public Public_Class {  
   void Test() {  
      Console::WriteLine("=======================");  
      Console::WriteLine("in function of derived class");  
      Protected_Function();  
      Protected_Private_Function();  
      Private_Protected_Function();  
      Console::WriteLine("exiting function of derived class");  
      Console::WriteLine("=======================");  
   }  
};  
```  
  
 El ejemplo siguiente utiliza el componente creado en el ejemplo anterior y, por tanto, muestra cómo tener acceso a los miembros desde fuera del ensamblado.  
  
```  
  
// compile with: /clr  
#using "type_member_visibility_2.dll"  
using namespace System;  
// a derived type, calls protected functions  
ref struct MyClass : public Public_Class {  
   void Test() {  
      Console::WriteLine("=======================");  
      Console::WriteLine("in function of derived class");  
      Protected_Function();  
      Protected_Public_Function();  
      Public_Protected_Function();  
      Console::WriteLine("exiting function of derived class");  
      Console::WriteLine("=======================");  
   }  
};  
  
int main() {  
   Public_Class ^ a = gcnew Public_Class;  
   MyClass ^ b = gcnew MyClass;  
   a->Public_Function();  
  
   // call protected functions  
   b->Test();  
  
   // can't be called outside the assembly  
   // a->Private_Function();  
   // a->Internal_Function();     
   // a->Protected_Private_Function();  
   // a->Private_Protected_Function();  
}  
```  
  
 **Salida**  
  
```Output  
in Public_Function  
=======================  
in function of derived class  
in Protected_Function  
in Protected_Public_Function  
in Public_Protected_Function  
exiting function of derived class  
=======================  
```  
  
##  <a name="BKMK_Public_and_private_native_classes"></a> Clases nativas públicas y privadas  
 Un tipo nativo puede hacer referencia a un tipo administrado.  Por ejemplo, una función de un tipo administrado puede tomar un parámetro cuyo tipo sea un struct nativo.  Si el tipo administrado y la función son públicos en un ensamblado, el tipo nativo también debe ser público.  
  
```  
  
// native type  
public struct N {  
   N(){}  
   int i;  
};  
```  
  
 A continuación, cree el archivo de código fuente que utiliza el tipo nativo:  
  
```  
  
// compile with: /clr /LD  
#include "mcppv2_ref_class3.h"  
// public managed type  
public ref struct R {  
   // public function that takes a native type  
   void f(N nn) {}  
};  
```  
  
 Ahora, compile un cliente:  
  
```  
  
// compile with: /clr  
#using "mcppv2_ref_class3.dll"  
  
#include "mcppv2_ref_class3.h"  
  
int main() {  
   R ^r = gcnew R;  
   N n;  
   r->f(n);  
}  
```  
  
##  <a name="BKMK_Static_constructors"></a> Constructores estáticos  
 Un tipo CLR, por ejemplo, una clase o struct, puede tener un constructor estático que se puede utilizar para inicializar los miembros de datos estáticos.  A un constructor estático se le llama a lo sumo una vez y solo antes de tener acceso a un miembro estático del tipo por primera vez.  
  
 Un constructor de instancia siempre se ejecuta después de un constructor estático.  
  
 El compilador no puede alinear una llamada a un constructor si la clase tiene un constructor estático.  El compilador no puede alinear una llamada a ningún miembro de función si la clase es un tipo de valor, tiene un constructor estático y no tiene un constructor de instancia.  CLR puede alinear la llamada, pero el compilador no puede.  
  
 Defina un constructor estático como función miembro privada, porque está diseñado para que solo lo llame CLR.  
  
 Para obtener más información sobre los constructores estáticos, vea [Cómo: definir un Constructor estático de interfaz (C++ / CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) .  
  
```  
  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
private:  
   static int i = 0;  
  
   static MyClass() {  
      Console::WriteLine("in static constructor");  
      i = 9;  
   }  
  
public:  
   static void Test() {  
      i++;  
      Console::WriteLine(i);  
   }  
};  
  
int main() {  
   MyClass::Test();  
   MyClass::Test();  
}  
```  
  
 **Salida**  
  
```Output  
in static constructor  
10  
11  
```  
  
##  <a name="BKMK_Semantics_of_the_this_pointer"></a> Semántica de este puntero  
 Cuando se usa Visual C++ para definir tipos, el puntero `this` en un tipo de referencia es de tipo “identificador”. El puntero `this` en un tipo de valor es de tipo “puntero interior”.  
  
 Estas semánticas diferentes del puntero `this` pueden provocar un comportamiento inesperado cuando se llama a un indizador predeterminado. El ejemplo siguiente muestra la manera correcta de tener acceso a un indizador predeterminado en un tipo de referencia y un tipo de valor.  
  
 Para obtener más información, consulte  
  
-   [Identificador a un operador de objeto (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)  
  
-   [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)  
  
```  
  
// compile with: /clr  
using namespace System;  
  
ref struct A {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
  
   A() {  
      // accessing default indexer  
      Console::WriteLine("{0}", this[3.3]);  
   }  
};  
  
value struct B {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
   void Test() {  
      // accessing default indexer  
      Console::WriteLine("{0}", this->default[3.3]);  
   }  
};  
  
int main() {  
   A ^ mya = gcnew A();  
   B ^ myb = gcnew B();  
   myb->Test();  
}  
```  
  
 **Salida**  
  
```Output  
10.89  
10.89  
```  
  
##  <a name="BKMK_Hide_by_signature_functions"></a> Funciones de ocultación por signatura  
 En C++ estándar, una función de una clase base se oculta con una función que tiene el mismo nombre en una clase derivada, incluso si la función de la clase derivada no tiene el mismo número o el mismo tipo de parámetros. Esto se conoce como *ocultar por nombre* semántica. En un tipo de referencia, una función de una clase base solo se puede ocultar con una función de una clase derivada si el nombre y la lista de parámetros son iguales. Esto se conoce como *oculta por signatura* semántica.  
  
 Una clase se considera oculta por signatura cuando todas sus funciones se marcan en los metadatos como `hidebysig`. De forma predeterminada, todas las clases que se crean en **/CLR** tienen `hidebysig` funciones. Cuando una clase tiene funciones `hidebysig`, el compilador no oculta las funciones por nombre en ninguna clase base directa, pero si el compilador encuentra una clase oculta por nombre en una cadena de herencia, continúa ese comportamiento de ocultar por nombre.  
  
 Con una semántica oculta por signatura, cuando se llama a una función en un objeto, el compilador identifica la clase derivada que contiene una función que podría satisfacer la llamada de función. Si solo hay una función en la clase que pueda satisfacer la llamada, el compilador llama a esa función. Si hay más de una función en la clase que podría satisfacer la llamada, el compilador utiliza las reglas de resolución de sobrecarga para determinar a qué función se debe llamar. Para obtener más información acerca de las reglas de sobrecarga, consulte [sobrecarga de funciones](../cpp/function-overloading.md).  
  
 Para una llamada de función dada, una función de una clase base podría tener una signatura que crea una coincidencia ligeramente mejor que una función de una clase derivada. Sin embargo, si se llama explícitamente a la función en un objeto de la clase derivada, se llama a la función de la clase derivada.  
  
 Dado que el valor devuelto no se considera parte de la signatura de una función, se oculta una función de clase base si tiene el mismo nombre y el mismo número y tipo argumentos que una función de clase derivada, incluso si el tipo de valor devuelto es diferente.  
  
 El ejemplo siguiente muestra que una función de una clase derivada no oculta una función en una clase base.  
  
```  
  
// compile with: /clr  
using namespace System;  
ref struct Base {  
   void Test() {   
      Console::WriteLine("Base::Test");   
   }  
};  
  
ref struct Derived : public Base {  
   void Test(int i) {   
      Console::WriteLine("Derived::Test");   
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
   // Test() in the base class will not be hidden  
   t->Test();  
}  
```  
  
 **Salida**  
  
```Output  
Base::Test  
```  
  
 El ejemplo siguiente muestra que el compilador de Visual C++ llama a una función de la clase más derivada (aunque se requiera una conversión para que uno o varios parámetros coincidan) y no llama a una función de una clase base que es una coincidencia mejor para la llamada de función.  
  
```  
  
// compile with: /clr  
using namespace System;  
ref struct Base {  
   void Test2(Single d) {   
      Console::WriteLine("Base::Test2");   
   }  
};  
  
ref struct Derived : public Base {  
   void Test2(Double f) {   
      Console::WriteLine("Derived::Test2");   
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
   // Base::Test2 is a better match, but the compiler  
   // calls a function in the derived class if possible  
   t->Test2(3.14f);  
}  
```  
  
 **Salida**  
  
```Output  
Derived::Test2  
```  
  
 El ejemplo siguiente muestra que es posible ocultar una función incluso si la clase base tiene la misma signatura que la clase derivada.  
  
```  
  
// compile with: /clr  
using namespace System;  
ref struct Base {  
   int Test4() {   
      Console::WriteLine("Base::Test4");   
      return 9;   
   }  
};  
  
ref struct Derived : public Base {  
   char Test4() {   
      Console::WriteLine("Derived::Test4");   
      return 'a';   
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
  
   // Base::Test4 is hidden  
   int i = t->Test4();  
   Console::WriteLine(i);  
}  
```  
  
 **Salida**  
  
```Output  
Derived::Test4  
97  
```  
  
##  <a name="BKMK_Copy_constructors"></a> Constructores de copias  
 El estándar de C++ indica que se debe llamar a un constructor de copias cuando se mueve un objeto, de forma que un objeto se crea y se destruye en la misma dirección.  
  
 Sin embargo, cuando **/CLR** se utiliza para compilar y una función compilada para MSIL llama a una función nativa donde una clase nativa, o más de uno, se pasa por valor y donde la clase nativa tiene un constructor de copias y el destructor, ninguna copia se llama al constructor y el objeto se destruye en una dirección diferente de aquella donde se creó. Esto podría producir problemas si la clase tiene un puntero a sí misma o si el código realiza el seguimiento de los objetos por dirección.  
  
 Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 El ejemplo siguiente muestra cuándo no se genera un constructor de copias.  
  
```  
  
// compile with: /clr  
#include<stdio.h>  
  
struct S {  
   int i;  
   static int n;  
  
   S() : i(n++) {   
      printf_s("S object %d being constructed, this=%p\n", i, this);   
   }  
  
   S(S const& rhs) : i(n++) {   
      printf_s("S object %d being copy constructed from S object "  
               "%d, this=%p\n", i, rhs.i, this);   
   }  
  
   ~S() {  
      printf_s("S object %d being destroyed, this=%p\n", i, this);   
   }  
};  
  
int S::n = 0;  
  
#pragma managed(push,off)  
void f(S s1, S s2) {  
   printf_s("in function f\n");  
}  
#pragma managed(pop)  
  
int main() {  
   S s;  
   S t;  
   f(s,t);  
}  
```  
  
 **Salida**  
  
```Output  
S object 0 being constructed, this=0018F378  
S object 1 being constructed, this=0018F37C  
S object 2 being copy constructed from S object 1, this=0018F380  
S object 3 being copy constructed from S object 0, this=0018F384  
S object 4 being copy constructed from S object 2, this=0018F2E4  
S object 2 being destroyed, this=0018F380  
S object 5 being copy constructed from S object 3, this=0018F2E0  
S object 3 being destroyed, this=0018F384  
in function f  
S object 5 being destroyed, this=0018F2E0  
S object 4 being destroyed, this=0018F2E4  
S object 1 being destroyed, this=0018F37C  
S object 0 being destroyed, this=0018F378  
```  
  
##  <a name="BKMK_Destructors_and_finalizers"></a> Destructores y finalizadores  
 Los destructores de un tipo de referencia realizan una limpieza determinista de recursos. Los finalizadores limpian los recursos no administrados y puede llamarlos de forma determinista el destructor o de forma no determinista el recolector de elementos no utilizados. Para obtener información acerca de los destructores de C++ estándar, consulte [destructores](../cpp/destructors-cpp.md).  
  
```  
class classname {  
   ~classname() {}   // destructor  
   ! classname() {}   // finalizer  
};  
```  
  
 El comportamiento de destructores en una clase administrada de Visual C++ es diferente al de las Extensiones administradas para C++. Para obtener más información acerca de este cambio, consulte [cambios en la semántica de los destructores](../dotnet/changes-in-destructor-semantics.md).  
  
 El recolector de elementos no utilizados de CLR elimina los objetos no utilizados y libera la memoria que usan cuando ya no son necesarios. Sin embargo, un tipo puede utilizar los recursos que el recolector de elementos no utilizados no sabe liberar. Estos recursos se conocen como recursos no administrados (por ejemplo, los identificadores de archivos nativos). Se recomienda liberar todos los recursos no administrados en el finalizador. Dado que el recolector de elementos no utilizados libera los recursos administrados de forma no determinista, no es seguro hacer referencia a los recursos administrados en un finalizador porque es posible que el recolector de elementos no utilizados haya limpiado ese recurso administrado.  
  
 Un finalizador de Visual C++ no es igual que el método <xref:System.Object.Finalize%2A>. (En la documentación de CLR, el finalizador y el método <xref:System.Object.Finalize%2A> se usan como sinónimos). El recolector de elementos no utilizados llama al método <xref:System.Object.Finalize%2A>, que invoca cada finalizador en una cadena de herencia de la clase. A diferencia de los destructores de Visual C++, una llamada al finalizador de clases derivadas no hace que el compilador invoque el finalizador en todas las clases base.  
  
 Dado que el compilador de Visual C++ admite que los recursos se liberen de forma determinista, no intente implementar los métodos <xref:System.IDisposable.Dispose%2A> o <xref:System.Object.Finalize%2A>. Sin embargo, si está familiarizado con estos métodos, a continuación se muestra cómo se asignan un finalizador de Visual C++ y el destructor que llama al finalizador al patrón de <xref:System.IDisposable.Dispose%2A>:  
  
```  
// Visual C++ code  
ref class T {  
   ~T() { this->!T(); }   // destructor calls finalizer  
   !T() {}   // finalizer  
};  
  
// equivalent to the Dispose pattern  
void Dispose(bool disposing) {  
   if (disposing) {  
      ~T();  
   } else {  
      !T();  
   }  
}  
```  
  
 Un tipo administrado puede utilizar también recursos administrados que sería preferible liberar de forma determinista, y no dejar que el recolector de elementos no utilizados los libere de forma no determinista en algún momento después de que el objeto no se necesite. La liberación determinista de recursos puede mejorar significativamente el rendimiento.  
  
 El compilador de Visual C++ permite la definición de un destructor para limpiar objetos de forma determinista. Utilice el destructor para liberar todos los recursos que desee liberar de forma determinista.  Si hay un finalizador, llámelo desde el destructor para evitar la duplicación del código.  
  
```  
  
// compile with: /clr /c  
ref struct A {  
   // destructor cleans up all resources  
   ~A() {  
      // clean up code to release managed resource  
      // ...  
      // to avoid code duplication,   
      // call finalizer to release unmanaged resources  
      this->!A();  
   }  
  
   // finalizer cleans up unmanaged resources  
   // destructor or garbage collector will  
   // clean up managed resources  
   !A() {  
      // clean up code to release unmanaged resources  
      // ...  
   }  
};  
```  
  
 Si el código que utiliza el tipo no llama al destructor, el recolector de elementos no utilizados libera finalmente todos los recursos administrados.  
  
 La presencia de un destructor no implica la presencia de un finalizador. Sin embargo, la presencia de un finalizador implica que se debe definir un destructor y llamar al finalizador desde el destructor. Esto hace que los recursos no administrados se liberen de forma determinista.  
  
 Llamar al destructor suprime (mediante <xref:System.GC.SuppressFinalize%2A>) la finalización del objeto. Si no se llama al destructor, el recolector de elementos no utilizados llamará finalmente al finalizador del tipo.  
  
 Limpiar los recursos de objeto de forma determinista llamando al destructor puede mejorar el rendimiento en comparación con dejar que CLR finalice el objeto de forma no determinista.  
  
 Código que ha escrito en Visual C++ y compilado mediante **/CLR** ejecuta el destructor del tipo si:  
  
-   Un objeto creado mediante la semántica de la pila sale del ámbito. Para obtener más información, consulte [semántica de pila de C++ para los tipos de referencia](../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
-   Se produce una excepción durante la construcción del objeto.  
  
-   El objeto es miembro de un objeto cuyo destructor está en ejecución.  
  
-   Se llama a la [eliminar](../cpp/delete-operator-cpp.md) operador en un identificador ([identificador a un operador de objeto (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)).  
  
-   Se llama explícitamente al destructor.  
  
 Si el tipo lo consume un cliente escrito en otro lenguaje, se llama al destructor de la forma siguiente:  
  
-   En una llamada a <xref:System.IDisposable.Dispose%2A>.  
  
-   En una llamada a `Dispose(void)` en el tipo.  
  
-   Si el tipo sale de ámbito en una instrucción `using` de C#.  
  
 Si crea un objeto de un tipo de referencia en el montón administrado (no mediante la semántica de pila para los tipos de referencia), use [try-finally](../cpp/try-finally-statement.md) sintaxis para asegurarse de que una excepción no impide que el destructor no se ejecuten.  
  
```  
  
// compile with: /clr  
ref struct A {  
   ~A() {}  
};  
  
int main() {  
   A ^ MyA = gcnew A;  
   try {  
      // use MyA  
   }  
   finally {  
      delete MyA;  
   }  
}  
```  
  
 Si el tipo tiene un destructor, el compilador genera un método `Dispose` que implementa <xref:System.IDisposable>. Si un tipo escrito en Visual C++ tiene un destructor que se utiliza en otro lenguaje, una llamada a `IDisposable::Dispose` en ese tipo hace que se llame al destructor del tipo. Cuando el tipo se usa desde un cliente de Visual C++, no puede llamar directamente a `Dispose`; en su lugar, llame al destructor mediante el operador `delete`.  
  
 Si el tipo tiene un finalizador, el compilador genera un método `Finalize(void)` que invalida <xref:System.Object.Finalize%2A>.  
  
 Si un tipo tiene un finalizador o un destructor, el compilador genera un método `Dispose(bool)`, según el patrón de diseño. (Para obtener información, consulte [patrón Dispose](/dotnet/standard/design-guidelines/dispose-pattern)). `Dispose(bool)` no se puede crear o llamar explícitamente en Visual C++.  
  
 Si un tipo tiene una clase base que se ajusta al patrón de diseño, se llama a los destructores de todas las clases base cuando se llama al destructor de la clase derivada. (Si el tipo está escrito en Visual C++, el compilador garantiza que los tipos implementen este patrón). Es decir, el destructor de una clase de referencia se encadena a sus bases y miembros tal como especifica el estándar C++: primero se ejecuta el destructor de la clase, después los destructores para sus miembros en el orden inverso al que se construyeron y, finalmente, los destructores para las clases base en el orden inverso al que se construyeron.  
  
 Los destructores y los finalizadores no se permiten dentro de los tipos o interfaces de valor.  
  
 Un finalizador solo se puede definir o declarar en un tipo de referencia. Igual que un constructor y un destructor, un finalizador no tiene ningún tipo de valor devuelto.  
  
 Una vez que se ejecuta el finalizador de un objeto, también se llama a los finalizadores de las clases base, empezando por el tipo menos derivado. Los finalizadores para los miembros de datos no se encadenan automáticamente al finalizador de la clase.  
  
 Si un finalizador elimina un puntero nativo en un tipo administrado, debe asegurarse de que las referencias o a través del puntero nativo no se recopilen prematuramente; llame al destructor en el tipo administrado en lugar de utilizar <xref:System.GC.KeepAlive%2A>.  
  
 En tiempo de compilación, puede detectar si un tipo tiene un finalizador o un destructor. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 El ejemplo siguiente muestra dos tipos, uno con recursos no administrados y otro con recursos administrados que se liberan de forma determinista.  
  
```  
  
// compile with: /clr  
#include <vcclr.h>  
#include <stdio.h>  
using namespace System;  
using namespace System::IO;  
  
ref class SystemFileWriter {  
   FileStream ^ file;  
   array<Byte> ^ arr;  
   int bufLen;  
  
public:  
   SystemFileWriter(String ^ name) : file(File::Open(name, FileMode::Append)),   
                                     arr(gcnew array<Byte>(1024)) {}  
  
   void Flush() {  
      file->Write(arr, 0, bufLen);  
      bufLen = 0;  
   }  
  
   ~SystemFileWriter() {  
      Flush();  
      delete file;  
   }  
};  
  
ref class CRTFileWriter {  
   FILE * file;  
   array<Byte> ^ arr;  
   int bufLen;  
  
   static FILE * getFile(String ^ n) {  
      pin_ptr<const wchar_t> name = PtrToStringChars(n);  
      FILE * ret = 0;  
      _wfopen_s(&ret, name, L"ab");  
      return ret;  
   }  
  
public:  
   CRTFileWriter(String ^ name) : file(getFile(name)), arr(gcnew array<Byte>(1024) ) {}  
  
   void Flush() {  
      pin_ptr<Byte> buf = &arr[0];  
      fwrite(buf, 1, bufLen, file);  
      bufLen = 0;  
   }  
  
   ~CRTFileWriter() {  
      this->!CRTFileWriter();  
   }  
  
   !CRTFileWriter() {  
      Flush();  
      fclose(file);  
   }  
};  
  
int main() {  
   SystemFileWriter w("systest.txt");  
   CRTFileWriter ^ w2 = gcnew CRTFileWriter("crttest.txt");  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases y estructuras](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)