---
title: "Clases y structs (Extensiones de componentes de C++) | Microsoft Docs"
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
  - "public"
  - "ref struct"
  - "value_CPP"
  - "ref class"
  - "value struct"
  - "ref struct_cpp"
  - "ref class_cpp"
  - "value class_cpp"
  - "value struct_cpp"
  - "value class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ref class (palabra clave) [C++]"
  - "ref struct (palabra clave) [C++]"
  - "value y class (palabras clave) [C++]"
  - "value y struct (palabras clave) [C++]"
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases y structs (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Declara una clase o struct cuya *duración de objetos* se administra automáticamente.  Cuando el objeto ya no es accesible o se sale del ámbito, Visual C\+\+ descarta automáticamente la memoria asignada al objeto.  
  
## Todos los runtimes  
 **Sintaxis**  
  
```  
  
          class_access ref class    name modifier :  inherit_access base_type {};  
class_access ref struct   name modifier :  inherit_access base_type {};  
class_access value class  name modifier :  inherit_access base_type {};  
class_access value struct name modifier :  inherit_access base_type {};  
  
```  
  
 **Parámetros**  
  
 *class\_access* \(opcional\)  
 La accesibilidad de la clase o struct fuera del ensamblado.  Los valores posibles son **public** y `private` \(`private` es el valor predeterminado\).  Las clases anidadas o los structs no pueden tener un especificador *class\_access*.  
  
 *name*  
 Nombre de la clase o struct.  
  
 *modifier* \(opcional\)  
 [abstract](../windows/abstract-cpp-component-extensions.md) y [sealed](../windows/sealed-cpp-component-extensions.md) son modificadores válidos.  
  
 *inherit\_access* \(opcional\)  
 Accesibilidad de `base_type`.  La única accesibilidad permitida es `public` \(`public` es el valor predeterminado\).  
  
 *base\_type* \(opcional\)  
 Tipo base.  Sin embargo, un tipo de valor no puede actuar como tipo base.  
  
 Para obtener más información, vea las descripciones específicas del lenguaje correspondientes a este parámetro que aparecen en las secciones [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)].  
  
 **Comentarios**  
  
 La accesibilidad de miembro predeterminada de un objeto declarado con **ref class** o **value class** es `private`,  mientras que la accesibilidad de miembro predeterminada de un objeto declarado con **ref struct** o **value struct** es `public`.  
  
 Cuando un tipo de referencia se hereda de otro tipo de referencia, las funciones virtuales de la clase base deben reemplazarse explícitamente \(con [override](../windows/override-cpp-component-extensions.md)\) u ocultarse \(con [new \(nueva ranura en vtable\)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)\).  Las funciones de la clase derivada también deben marcarse explícitamente como `virtual`.  
  
 Para detectar en tiempo de compilación si un tipo es `ref class` o `ref struct`, o `value class` o `value struct`, use `__is_ref_class (``type``)`, `__is_value_class (``type``)` o  `__is_simple_value_class (``type``)`.  Para obtener más información, consulte [Compatibilidad de compilador para type traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 Para obtener más información sobre clases y structs, vea  
  
-   [Crear instancias de clases y structs](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)  
  
-   [Semántica del puntero this en los tipos de valor y de referencia](../misc/semantics-of-the-this-pointer-in-value-and-reference-types.md)  
  
-   [Semántica de pila de C\+\+ para los tipos de referencia](../dotnet/cpp-stack-semantics-for-reference-types.md)  
  
-   [Clases, estructuras y uniones](../cpp/classes-and-structs-cpp.md)  
  
-   [Clases nativas públicas y privadas](../misc/how-to-declare-public-and-private-on-native-classes.md)  
  
-   [Clases abstractas implícitamente](../misc/implicitly-abstract-classes.md)  
  
-   [Definir constructores estáticos en una clase o struct](../misc/how-to-define-static-constructors-in-a-class-or-struct.md)  
  
-   [El constructor de copia podría no generarse](../misc/copy-constructor-may-not-be-generated.md)  
  
-   [Funciones de ocultación por signatura en los tipos de referencia](../misc/hide-by-signature-functions-in-reference-types.md)  
  
-   [Destructores y finalizadores de Visual C\+\+](../misc/destructors-and-finalizers-in-visual-cpp.md)  
  
-   [Visibilidad de tipos y de miembros](../misc/type-and-member-visibility.md)  
  
-   [Operadores definidos por el usuario](../dotnet/user-defined-operators-cpp-cli.md)  
  
-   [Conversiones definidas por el usuario](../dotnet/user-defined-conversions-cpp-cli.md)  
  
-   [Cómo: Envolver una clase nativa para utilizarla en C\#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
-   [Clases genéricas \(C\+\+\/CLI\)](../Topic/Generic%20Classes%20\(C++-CLI\).md)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **Comentarios**  
  
 Vea [Ref \(clases y structs\)](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx) y [Value \(clases y structs\)](http://msdn.microsoft.com/library/windows/apps/hh699861.aspx).  
  
 **Parámetros**  
  
 *base\_type* \(opcional\)  
 Tipo base.  `ref class` o `ref struct` pueden heredar de cero o más interfaces y de cero o un tipo `ref`.  `value class` o `value struct` solo pueden heredar de cero o más interfaces.  
  
 Al declarar un objeto mediante las palabras clave `ref class` o `ref struct`, se obtiene acceso al objeto con un identificador de objeto, es decir, un puntero de contador de referencias al objeto.  Cuando la variable declarada se sale del ámbito, el compilador elimina automáticamente el objeto subyacente.  Cuando el objeto se usa como parámetro en una llamada o se almacena en una variable, se pasa o se almacena realmente un identificador del objeto.  
  
 Cuando se declara un objeto mediante las palabras clave `value class` o `value struct`, la duración del objeto declarado no se supervisa.  El objeto es como cualquier otra clase o struct estándar de C\+\+.  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Comentarios**  
  
 En la tabla siguiente se enumeran las diferencias con la sintaxis mostrada en la sección **Todos los runtimes** que son específicas de C\+\+\/CLI.  
  
 **Parámetros**  
  
 *base\_type* \(opcional\)  
 Tipo base.  `ref class` o `ref struct` pueden heredar de cero o más interfaces administradas y de cero o un tipo ref.  `value class` o `value struct` solo pueden heredar de cero o más interfaces administradas.  
  
 Las palabras clave `ref class` y `ref struct` indican al compilador que la clase o estructura debe asignarse en el montón.  Cuando el objeto se usa como parámetro en una llamada o se almacena en una variable, se pasa o se almacena realmente una referencia al objeto.  
  
 Las palabras clave `value class` y `value struct` indican al compilador que el valor de la clase o estructura asignada se pasa a funciones o se almacena en miembros.  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)