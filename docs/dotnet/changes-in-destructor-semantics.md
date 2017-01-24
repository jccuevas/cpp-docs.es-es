---
title: "Cambios en la sem&#225;ntica de los destructores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "destructores, C++"
  - "finalizadores [C++]"
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cambios en la sem&#225;ntica de los destructores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La semántica de los destructores de clase ha cambiado significativamente de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 En Extensiones administradas, se permitía un destructor de clase dentro de una clase de referencia, pero no dentro de una clase de valor.  Esto no ha cambiado en la nueva sintaxis.  Sin embargo, la semántica del destructor de clase ha cambiado.  En este tema se abordan las razones de ese cambio y se explica cómo afecta a la traducción del código CLR existente.  Probablemente sea el cambio más importante en el nivel de programador entre las dos versiones del lenguaje.  
  
## Finalización no determinista  
 Antes de que el recolector de elementos no utilizados reclame la memoria asociada a un objeto, se invoca un método `Finalize` asociado, si existe.  Puede pensar en este método como una especie de superdestructor ya que no está vinculado a la duración del programa del objeto.  Esto se conoce como finalización.  El momento adecuado en el que se debe invocar un método `Finalize`, o si debe hacerse, es indefinido.  Esto es lo que se significa que la recolección de elementos no utilizados presenta una finalización no determinista.  
  
 La finalización no determinista funciona bien con la administración de memoria dinámica.  Cuando empieza a escasear la memoria disponible, se inicia el recolector de elementos no utilizados.  En un entorno en el que se recolectan los elementos no utilizados, los destructores para liberar memoria son innecesarios.  No obstante, la finalización no determinista no funciona bien si un objeto mantiene un recurso crítico como una conexión de base de datos o un bloqueo de algún tipo.  En este caso, hay que liberar dicho recurso lo antes posible.  En el universo nativo, esto se realiza utilizando un par formado por un constructor y un destructor.  Cuando finaliza la duración del objeto, ya sea cuando finaliza el bloque local dentro del que se declara o cuando se desenreda la pila debido a la generación de una excepción, se ejecuta el destructor y el recurso se libera automáticamente.  Este enfoque funciona muy bien y su ausencia en Extensiones administradas se echa mucho en falta.  
  
 La solución facilitada por el CLR es para una clase que implemente el método `Dispose` de la interfaz `IDisposable`.  El problema aquí es que `Dispose` requiere una invocación explícita por parte del usuario.  Esto puede llevar a errores.  El lenguaje de C\# proporciona un método modesto de automatización en forma de una instrucción `using` especial.  El diseño de Extensiones administradas no proporciona ninguna compatibilidad especial.  
  
## Destructores de Extensiones administradas para C\+\+  
 En Extensiones administradas, el destructor de una clase de referencia se implementa mediante el uso de los dos siguientes pasos:  
  
1.  El nombre del destructor proporcionado por el usuario cambia internamente a `Finalize`.  Si la clase tiene una clase base \(recuerde que bajo el Modelo de objetos del CLR sólo se admite la herencia simple\), el compilador inserta una llamada a su finalizador tras la ejecución del código proporcionado por el usuario.  Por ejemplo, considere la siguiente jerarquía simple tomada de la especificación del lenguaje de Extensiones administradas:  
  
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
  
 En este ejemplo, el nombre de ambos destructores se cambia por `Finalize`.  `Finalize` de `B` presenta una invocación al método `Finalize` de `A` agregado a continuación de la invocación de `WriteLine`.  Esto es lo que el recolector de elementos no utilizados invocará de forma predeterminada durante la finalización.  A continuación, se muestra cuál podría ser el aspecto de esta transformación interna:  
  
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
  
1.  En el segundo paso, el compilador sintetiza un destructor virtual.  Este destructor es lo que nuestros programas de usuario de Extensiones administradas invocan directamente o a través de la aplicación de la expresión de eliminación.  Nunca lo invoca el recolector de elementos no utilizados.  
  
     Se colocan dos instrucciones dentro de este destructor sintetizado.  La primera de ellas es una llamada a `GC::SuppressFinalize`, para asegurarse de que no haya más invocaciones a `Finalize`.  La segunda es la invocación real de `Finalize`, que representa el destructor proporcionado por usuario para esa clase.  A continuación se muestra cuál podría ser su aspecto:  
  
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
  
 Mientras que esta implementación permite al usuario invocar explícitamente el método `Finalize` de la clase, ahora mejor que en un momento en que no se tenga el control, realmente no concuerda con la solución del método `Dispose`.  Esto ha cambiado en [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
## Destructores en la nueva sintaxis  
 En la nueva sintaxis, el destructor cambia de nombre internamente al método `Dispose` y la clase de referencia se extiende automáticamente para implementar la interfaz `IDispose`.  Es decir, en [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)], nuestro par de clases se transforma del siguiente modo:  
  
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
  
 Cuando un destructor se invoca explícitamente en la nueva sintaxis, o cuando se aplica `delete` a un controlador de seguimiento, el método `Dispose` subyacente se invoca automáticamente.  Si es una clase derivada, una llamada del método `Dispose` de la clase base se insertan al cierre del método sintetizado.  
  
 Pero esto no nos conduce directamente a una finalización determinista.  Para alcanzarla, necesitamos compatibilidad adicional con objetos de referencia locales. \(Esto no tiene ninguna compatibilidad análoga dentro de Extensiones administradas, por lo que no es un problema de traducción\).  
  
## Declarar un objeto de referencia  
 [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)] admite la declaración de un objeto de una clase de referencia en la pila local o como miembro de una clase como si fuera accesible directamente.  Cuando se combina con la asociación del destructor mediante el método `Dispose`, el resultado es la invocación automatizada de la semántica de finalización en los tipos de referencia.  
  
 En primer lugar, definimos nuestra clase de referencia de forma que la creación de objetos funciona como la adquisición de un recurso a través de su constructor de clase.  En segundo lugar, dentro del destructor de clase, liberamos el recurso adquirido cuando se creó el objeto.  
  
```  
public ref class R {  
public:  
   R() { /* acquire expensive resource */ }  
   ~R() { /* release expensive resource */ }  
  
   // … everything else …  
};  
```  
  
 El objeto se declara localmente utilizando el nombre de tipo pero sin el sombrero de acompañamiento.  Todos los usos del objeto, como invocar un método, se efectúan a través del punto de selección de miembros \(`.`\) en lugar de la flecha \(`->`\).  Al final del bloque, se invoca automáticamente el destructor asociado, transformado en `Dispose`, tal y como se muestra a continuación:  
  
```  
void f() {  
   R r;   
   r.methodCall();  
  
   // r is automatically destructed here –  
   // that is, r.Dispose() is invoked  
}  
```  
  
 Al igual que ocurre con la instrucción `using` dentro de C\#, esto no supone ningún desafío para la restricción del CLR subyacente por la que todos los tipos de referencia deben asignarse en el montón CLR.  Las semántica subyacente permanece intacta.  El usuario podría haber escrito el siguiente equivalente \(se trata probablemente de la transformación interna llevada a cabo por el compilador\):  
  
```  
// equivalent implementation  
// except that it should be in a try/finally clause  
void f() {  
   R^ r = gcnew R;   
   r->methodCall();  
  
   delete r;  
}  
```  
  
 En efecto, en la nueva sintaxis, los destructores se vuelven a emparejar con los constructores como un mecanismo de adquisición\/liberación automatizado vinculado a la duración de un objeto local.  
  
## Declarar un método Finalize explícito  
 En la nueva sintaxis, como hemos visto, el destructor se sintetiza en el método `Dispose`.  Esto significa que cuando el destructor no se invoca explícitamente, el recolector de elementos no utilizados, durante la finalización, no encontrará como antes un método `Finalize` asociado para el objeto.  Para que se admita tanto la destrucción como la finalización, hemos introducido una sintaxis especial para proporcionar un finalizador.  Por ejemplo:  
  
```  
public ref class R {  
public:  
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }  
};  
```  
  
 El prefijo `!` es análogo a la tilde \(`~`\) que introduce un destructor de clase; es decir, ambos métodos posteriores a la duración tienen un símbolo \(token\) que precede al nombre de la clase.  Si el método `Finalize` sintetizado aparece dentro de una clase derivada, se insertará una invocación al método `Finalize` de clase base en su parte final.  Si el destructor se invoca explícitamente, se suprimirá el finalizador.  A continuación se muestra cuál podría ser el aspecto de la transformación:  
  
```  
// internal transformation under new syntax  
public ref class R {  
public:  
   void Finalize() {  
      Console::WriteLine( "I am the R::finalizer()!" );  
   }  
};   
```  
  
## Pasar de Extensiones administradas para C\+\+ a Visual C\+\+ 2010  
 El comportamiento en tiempo de ejecución de un programa de Extensiones administradas para C\+\+ se modifica al compilarlo en [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)] siempre que una clase de referencia contenga un destructor no trivial.  El algoritmo de traducción necesario es similar al siguiente:  
  
1.  Si existe un destructor, vuelva a escribir eso para que sea el finalizador de clase.  
  
2.  Si existe un método `Dispose`, vuelva a escribir eso en el destructor de clase.  
  
3.  Si existe un destructor pero no hay ningún método `Dispose`, retenga el destructor mientras lleva a cabo el primer elemento.  
  
 Al cambiar el código de Extensiones administradas a la nueva sintaxis, puede olvidarse de realizar esta transformación.  Si la aplicación dependía de algún modo de la ejecución de métodos de finalización asociados, el comportamiento de la aplicación diferirá silenciosamente del comportamiento esperado.  
  
## Vea también  
 [Tipos administrados \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [Destructores y finalizadores de Visual C\+\+](../misc/destructors-and-finalizers-in-visual-cpp.md)