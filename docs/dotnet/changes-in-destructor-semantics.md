---
title: Cambios en la semántica de los destructores | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- finalizers [C++]
- destructors, C++
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8a3d078300ca0e51ba8eb035d5428d300b0413a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33113205"
---
# <a name="changes-in-destructor-semantics"></a>Cambios en la semántica de los destructores
Semántica para los destructores de clase ha cambiado significativamente desde extensiones administradas para C++ a Visual C++.  
  
 En extensiones administradas, un destructor de clase se permite dentro de una clase de referencia, pero no dentro de una clase de valor. Esto no ha cambiado en la nueva sintaxis. Sin embargo, la semántica del destructor de clase ha cambiado. En este tema se centra en las razones de ese cambio y se explica cómo afecta a la traducción del código CLR existente. Es probable que el cambio de nivel de programador más importante entre las dos versiones del lenguaje.  
  
## <a name="non-deterministic-finalization"></a>Finalización no determinista  
 Antes de la memoria asociada con un objeto sea reclamada por el recolector de elementos no utilizados, un asociado `Finalize` método, si está presente, se invoca. Se puede considerar este método como una especie de superdestructor porque no está asociado a la duración de programa del objeto. Esto se conoce como finalización. El tiempo de solo cuando o incluso si un `Finalize` se invoca el método no está definido. Esto es lo que denominamos cuando decimos que la recolección de elementos utilizados presenta una finalización no determinista.  
  
 La finalización no determinista funciona bien con la administración de memoria dinámica. Cuando la memoria disponible pasa a ser escasa, inicia el recolector de elementos no utilizados. En un elementos no utilizados recopilan entorno, los destructores para liberar memoria son innecesarios. La finalización no determinista no funciona bien, sin embargo, si un objeto mantiene un recurso crítico como una conexión de base de datos o un bloqueo de algún tipo. En este caso, hay que liberar dicho recurso tan pronto como sea posible. En el mundo nativo, que se consigue mediante un par de constructor o destructor. Tan pronto como finaliza la vigencia del objeto, cuando finaliza el bloque local dentro del que se declara o cuando la pila unravels debido a una excepción, se ejecuta el destructor y el recurso se libera automáticamente. Este enfoque funciona muy bien y su ausencia en extensiones administradas se echa mucho en falta.  
  
 La solución proporcionada por el CLR es para que una clase implementar el `Dispose` método de la `IDisposable` interfaz. El problema es que `Dispose` requiere una invocación explícita por el usuario. Esto es propensa a errores. El lenguaje C# proporciona un método modesto de automatización en forma de una clase especial `using` instrucción. El diseño de extensiones administradas no proporciona ninguna compatibilidad especial.  
  
## <a name="destructors-in-managed-extensions-for-c"></a>Destructores de extensiones administradas para C++  
 En extensiones administradas, el destructor de una clase de referencia se implementa mediante el uso de los dos pasos siguientes:  
  
1.  El destructor proporcionado por el usuario se cambia el nombre internamente a `Finalize`. Si la clase tiene una clase base (Recuerde, bajo el modelo de objetos CLR, se admite la herencia única solo), el compilador inserta una llamada a su finalizador tras la ejecución del código proporcionado por el usuario. Por ejemplo, considere la siguiente jerarquía simple tomada de la especificación del lenguaje de extensiones administradas:  
  
```  
__gc class A {  
public:  
   ~A() { Console::WriteLine(S"in ~A"); }  
};  
  
__gc class B : public A {  
public:  
   ~B() { Console::WriteLine(S"in ~B");  }  
};  
```  
  
 En este ejemplo, ambos destructores se cambia el nombre `Finalize`. `B`del `Finalize` tiene una invocación de `A`del `Finalize` método agregado después de la invocación de `WriteLine`. Esto es lo que el recolector de elementos no utilizados de forma predeterminada invocará durante la finalización. Este es el aspecto que podría tener esta transformación interna:  
  
```  
// internal transformation of destructor under Managed Extensions  
__gc class A {  
public:  
   void Finalize() { Console::WriteLine(S"in ~A"); }  
};  
  
__gc class B : public A {  
public:  
   void Finalize() {   
      Console::WriteLine(S"in ~B");  
      A::Finalize();   
   }  
};  
```  
  
1.  En el segundo paso, el compilador sintetiza un destructor virtual. Este destructor es lo que nuestros programas de usuario de extensiones administradas invocan directamente o a través de una aplicación de la expresión de eliminación. Nunca se invoca por el recolector de elementos no utilizados.  
  
     Se colocan dos instrucciones dentro de este destructor sintetizada. Uno es una llamada a `GC::SuppressFinalize` para asegurarse de que no hay ningún más invocaciones de `Finalize`. La segunda es la invocación real de `Finalize`, que representa el destructor proporcionado por el usuario para esa clase. Este es el aspecto que podría:  
  
```  
__gc class A {  
public:  
   virtual ~A() {  
      System::GC::SuppressFinalize(this);  
      A::Finalize();  
   }  
};  
  
__gc class B : public A {  
public:  
   virtual ~B() {  
      System::GC::SuppressFinalize(this);  
      B::Finalize();  
   }  
};  
```  
  
 Aunque esta implementación permite al usuario invocar explícitamente de la clase `Finalize` método ahora en lugar de a la vez tenemos control alguno, realmente no concuerda con el `Dispose` solución del método. Esto ha cambiado en Visual C++.  
  
## <a name="destructors-in-new-syntax"></a>Destructores en la nueva sintaxis  
 En la nueva sintaxis, el destructor se cambia el nombre internamente en el `Dispose` método y la clase de referencia se extiende automáticamente para implementar la `IDispose` interfaz. Es decir, en Visual C++, nuestro par de clases se transforma como sigue:  
  
```  
// internal transformation of destructor under the new syntax  
__gc class A : IDisposable {  
public:  
   void Dispose() {   
      System::GC::SuppressFinalize(this);  
      Console::WriteLine( "in ~A");  
   }  
};  
  
__gc class B : public A {  
public:  
   void Dispose() {   
      System::GC::SuppressFinalize(this);  
      Console::WriteLine( "in ~B");    
      A::Dispose();   
   }  
};  
```  
  
 Cuando un destructor se invoca explícitamente en la nueva sintaxis, o cuando `delete` se aplica a un controlador de seguimiento, subyacente `Dispose` método se invoca automáticamente. Si es una clase derivada, una llamada de la `Dispose` método de la clase base se inserta al final del método sintetizado.  
  
 Pero esto no nos conduce a una finalización determinista. Para alcanzarla, necesitamos compatibilidad adicional de objetos de referencia local. (Esto tiene ninguna compatibilidad análoga dentro de extensiones administradas, y por lo que no es un problema de traducción).  
  
## <a name="declaring-a-reference-object"></a>Declarar un objeto de referencia  
 Visual C++ admite la declaración de un objeto de una clase de referencia en la pila local o como miembro de una clase como si fuera accesible directamente. Cuando se combina con la asociación del destructor con el `Dispose` método, el resultado es la invocación automatizada de la semántica de finalización en tipos de referencia.  
  
 En primer lugar, definimos nuestra clase de referencia de forma que la creación de objetos funciona como la adquisición de un recurso a través de su constructor de clase. En segundo lugar, en el destructor de clase, publicamos el recurso adquirido cuando se creó el objeto.  
  
```  
public ref class R {  
public:  
   R() { /* acquire expensive resource */ }  
   ~R() { /* release expensive resource */ }  
  
   // everything else...  
};  
```  
  
 El objeto se declara localmente mediante el nombre de tipo pero sin el sombrero de acompañamiento. Todos los usos del objeto, como la invocación de un método, se realizan a través del punto de selección de miembro (`.`) en lugar de flecha (`->`). Al final del bloque, el destructor asociado, se transforma en `Dispose`, se invoca automáticamente, como se muestra aquí:  
  
```  
void f() {  
   R r;   
   r.methodCall();  
  
   // r is automatically destructed here -  
   // that is, r.Dispose() is invoked  
}  
```  
  
 Al igual que con el `using` instrucción en C#, esto no supone ningún desafío la restricción CLR subyacente que todos los tipos de referencia deben asignarse en el montón CLR. La semántica subyacente permanece intacta. El usuario podría haber escrito equivalente lo siguiente (y es probable que la transformación interna realizada por el compilador):  
  
```  
// equivalent implementation  
// except that it should be in a try/finally clause  
void f() {  
   R^ r = gcnew R;   
   r->methodCall();  
  
   delete r;  
}  
```  
  
 En efecto, en la nueva sintaxis, los destructores se vuelven a emparejar con constructores como una adquisición y liberación automatizado mecanismo se vincula a un objeto local.  
  
## <a name="declaring-an-explicit-finalize"></a>Declarar un método Finalize explícito  
 En la nueva sintaxis, como hemos visto, el destructor se sintetizada en el `Dispose` método. Esto significa que cuando el destructor no se invoca explícitamente, el recolector de elementos no utilizados, durante la finalización, no como antes encontrará asociada `Finalize` método para el objeto. Para admitir la destrucción y la finalización, hemos introducido una sintaxis especial para proporcionar un finalizador. Por ejemplo:  
  
```  
public ref class R {  
public:  
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }  
};  
```  
  
 El `!` prefijo es análogo a la tilde (`~`), se introduce un destructor de clase, es decir, ambos métodos posteriores a la duración tienen un token de prefijo del nombre de la clase. Si el sintetizada `Finalize` método se produce dentro de una clase derivada, una invocación de la clase base `Finalize` método se inserta en su extremo. Si el destructor se invoca explícitamente, se suprime el finalizador. Este es el aspecto que podría tener la transformación:  
  
```  
// internal transformation under new syntax  
public ref class R {  
public:  
   void Finalize() {  
      Console::WriteLine( "I am the R::finalizer()!" );  
   }  
};   
```  
  
## <a name="moving-from-managed-extensions-for-c-to-visual-c-2010"></a>Mover desde extensiones administradas para C++ a Visual C++ 2010  
 El comportamiento en tiempo de ejecución de extensiones administradas de programa de C++ se cambia cuando se compila en Visual C++ cada vez que una clase de referencia contiene un destructor no trivial. El algoritmo de traducción que sea necesaria es similar al siguiente:  
  
1.  Si hay un destructor, vuelva a escribir eso para que sea el finalizador de la clase.  
  
2.  Si un `Dispose` método está presente, vuelva a escribir eso en el destructor de clase.  
  
3.  Si un destructor está presente pero no hay ningún `Dispose` método, retenga el destructor mientras se realiza el primer elemento.  
  
 Para mover el código de las extensiones administradas para la nueva sintaxis, es posible que falte realizar esta transformación. Si la aplicación dependiera de alguna manera en la ejecución de métodos de finalización asociados, el comportamiento de la aplicación en modo silencioso será diferente de la que desea.  
  
## <a name="see-also"></a>Vea también  
 [Tipos administrados (C++ / CL)](../dotnet/managed-types-cpp-cl.md)   
 [Destructores y finalizadores en cómo: definir y utilizar clases y structs (C++ / CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)