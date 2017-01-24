---
title: "delegate (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "delegate_cpp"
  - "delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delegate (palabra clave) [C++]"
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# delegate (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Declara un tipo que representa un puntero a función.  
  
## Todos los runtimes  
 Tanto [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] como Common Language Runtime son compatibles con delegados.  
  
### Comentarios  
 `delegate` es una palabra clave contextual.  Para obtener más información, vea [Palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
 Para detectar en tiempo de compilación si un tipo es un delegado, use el rasgo de tipo de `__is_delegate()`.  Para obtener más información, vea [Compatibilidad de compilador para type traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
## Windows en tiempo de ejecución  
 C\+\+\/CX admite delegados con la sintaxis siguiente.  
  
### Sintaxis  
  
```cpp  
  
access delegate return-type delegate-type-identifier ([ parameters ])  
```  
  
### Parámetros  
 *access*  
 \(opcional\) La accesibilidad del delegado, que puede ser `public` \(valor predeterminado\) o `private`.  El prototipo de función también se puede calificar con las palabras clave `const` o `volatile`.  
  
 *return\-type*  
 El tipo de valor devuelto del prototipo de función.  
  
 *delegate\-type\-identifier*  
 Nombre de tipo del delegado declarado.  
  
 *parameters*  
 \(Opcional\) Tipos e identificadores del prototipo de función.  
  
### Comentarios  
 Utilice *delegate\-type\-identifier* para declarar un evento con el mismo prototipo que el delegado.  Para obtener más información, vea [Delegados \(C\+\+\/CX\)](../Topic/Delegates%20\(C++-CX\).md).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## Common Language Runtime  
 Common Language Runtime admite delegados con la sintaxis siguiente.  
  
### Sintaxis  
  
```cpp  
  
access delegate function_declaration  
```  
  
### Parámetros  
 *access*  
 \(opcional\) La accesibilidad del delegado fuera del ensamblado puede ser pública o privada.  El valor predeterminado es privado.  Dentro de una clase, un delegado puede tener cualquier accesibilidad.  
  
 *function\_declaration*  
 La firma de la función que se puede enlazar al delegado.  El tipo de valor devuelto de un delegado puede ser cualquier tipo administrado.  Por razones de interoperabilidad, se recomienda que el tipo de valor devuelto de un delegado sea un tipo de CLS.  
  
 Para definir un delegado independiente, el primer parámetro de *function\_declaration* debe ser el tipo de puntero de `this` para el objeto.  Para obtener más información, vea [Delegados sin enlazar](../misc/unbound-delegates.md).  
  
### Comentarios  
 Los delegados son de multidifusión: "puntero de función" se puede enlazar a uno o más métodos dentro de una clase administrada.  La palabra clave **delegate** define un tipo de delegado de multidifusión con una firma de método específica.  
  
 Un delegado también se puede enlazar a un método de una clase de valor, como un método estático.  
  
 El delegado tiene las siguientes características:  
  
-   Hereda de **System::MulticastDelegate**.  
  
-   Tiene un constructor que toma dos argumentos: un puntero a una clase administrada o **NULL** \(en el caso del enlace a un método estático\) y un método completo del tipo especificado.  
  
-   Tiene un método denominado `Invoke`, cuya signatura coincide con la signatura declarada del delegado.  
  
 Cuando se invoca un delegado, las funciones se llaman en el orden en el que se adjuntaron.  
  
 El valor devuelto de un delegado es el valor devuelto de la última función de miembro adjunta.  
  
 Los delegados no se pueden sobrecargar.  
  
 Los delegados pueden enlazarse o ser independientes.  
  
 Al crear instancias de un delegado enlazado, el primer argumento será una referencia de objeto.  El segundo argumento de una creación de instancia de delegado será la dirección de un método de un objeto de clase administrada o un puntero a un método de un tipo de valor.   El segundo argumento de una creación de instancia del delegado debe asignar al método el nombre de la sintaxis completa de ámbito de clase y aplicar el operador address\-of.  
  
 Al crear instancias de un delegado sin enlazar, el primer argumento será la dirección de un método de un objeto de clase administrada o un puntero a un método de un tipo de valor.   El argumento debe llamar al método con la sintaxis completa de ámbito de clase y aplicar el operador address\-of.  
  
 Al crear un delegado para una función estática o global, solo se requiere un parámetro: la función \(opcionalmente, la dirección de la función\).  
  
 Para obtener más información acerca de delegados, vea  
  
-   [Delegados sin enlazar](../misc/unbound-delegates.md)  
  
-   [Cómo: Definir y utilizar delegados](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)  
  
-   [Delegar a un miembro de una clase de valor](../misc/how-to-associate-delegates-to-members-of-a-value-class.md)  
  
-   [Delegar a una función no administrada](../misc/how-to-associate-delegates-to-unmanaged-functions.md)  
  
-   [Delegados compuestos](../misc/how-to-compose-delegates.md)  
  
-   [Cómo: Pasar un delegado^ a una función nativa que espera un puntero de función](../misc/how-to-pass-a-delegate-hat-to-a-native-function-expecting-a-function-pointer.md)  
  
-   [Delegados genéricos \(Visual C\+\+\)](../Topic/Generic%20Delegates%20\(Visual%20C++\).md)  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 El ejemplo siguiente muestra cómo declarar, inicializar e invocar delegados.  
  
```cpp  
// mcppv2_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare a delegate  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      Console::WriteLine("in func1 {0}", i);  
   }  
  
   void func2(int i) {  
      Console::WriteLine("in func2 {0}", i);  
   }  
  
   static void func3(int i) {  
      Console::WriteLine("in static func3 {0}", i);  
   }  
};  
  
int main () {  
   A ^ a = gcnew A;  
  
   // declare a delegate instance  
   MyDel^ DelInst;  
  
   // test if delegate is initialized  
   if (DelInst)  
      DelInst(7);  
  
   // assigning to delegate  
   DelInst = gcnew MyDel(a, &A::func1);  
  
   // invoke delegate  
   if (DelInst)  
      DelInst(8);  
  
   // add a function  
   DelInst += gcnew MyDel(a, &A::func2);  
  
   DelInst(9);  
  
   // remove a function  
   DelInst -= gcnew MyDel(a, &A::func1);  
  
   // invoke delegate with Invoke  
   DelInst->Invoke(10);  
  
   // make delegate to static function  
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);  
   StaticDelInst(11);  
}  
```  
  
 **Resultados**  
  
  **en func1 8**  
 **en func1 9**  
 **en func2 9**  
 **en func2 10**  
 **en static func3 11**   
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)