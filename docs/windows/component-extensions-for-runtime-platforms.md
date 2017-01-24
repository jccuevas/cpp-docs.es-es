---
title: "Extensiones de componentes para plataformas de tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "palabras clave [C++]"
  - "Extensiones administradas para C++, sintaxis de reemplazo"
  - "Visual C++, palabras clave"
  - "lo nuevo [C++], palabras clave"
  - "lo nuevo [C++], características del lenguaje"
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
caps.latest.revision: 77
caps.handback.revision: 77
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Extensiones de componentes para plataformas de tiempo de ejecuci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ proporciona extensiones de lenguaje para ayudarle a programar en plataformas del runtime.  Mediante [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]\), puede programar aplicaciones y componentes de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] que se compilan en código nativo.  Aunque puede crear aplicaciones de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] programando directamente en las interfaces COM de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] mediante [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)], puede usar constructores, excepciones y otras expresiones de programación moderna de C\+\+.  Para habilitar la programación en C\+\+ en un entorno de ejecución administrado en la plataforma .NET, puede usar [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)].  
  
 **Dos runtime, un conjunto de extensiones**  
  
 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] es un subconjunto de [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)].  Para las extensiones comunes a [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] y [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)], la semántica depende de si el destino es Common Language Runtime \(CLR\) o [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  Para compilar la aplicación para que se ejecute en [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)], especifique la opción del compilador **\/ZW**.  Para compilarlo para que se ejecute en CLR, especifique la opción del compilador **\/clr**.  Estos modificadores se establecen automáticamente cuando se usa Visual Studio para crear un proyecto.  
  
 Para obtener más información sobre cómo crear aplicaciones de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] en C\+\+, vea [Guía básica para aplicaciones de Windows en tiempo de ejecución con C\+\+](http://msdn.microsoft.com/library/windows/apps/hh700360.aspx).  
  
 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] extiende el estándar C\+\+ de ANSI\/ISO, y se define en la norma ECMA [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)].  Para obtener información, vea [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
## Palabras clave de tipo de datos  
 Las extensiones de lenguaje incluyen *palabras clave agregadas*, que son palabras clave que constan de dos tokens separados por espacios en blanco.  Los tokens pueden tener un significado cuando se usan por separado, y otro significado cuando se usan juntos.  Por ejemplo, la palabra “ref” es un identificador normal, y la palabra “clase” es una palabra clave que declara una clase nativa.  Pero cuando estas palabras se combinan para formar `ref class`, la palabra clave agregada resultante declara una entidad denominada *clase en tiempo de ejecución*.  
  
 Las extensiones también incluyen palabras clave *contextuales*.  Una palabra clave se trata como contextual en función del tipo de instrucción que la contenga, y de su posición en esa instrucción.  Por ejemplo, el token “property” puede ser un identificador, o puede declarar una clase especial de miembro de clase pública.  
  
 En la tabla siguiente se enumeran las palabras clave en la extensión del lenguaje C\+\+.  
  
|Palabra clave|Contextual|Finalidad|Referencia|  
|-------------------|----------------|---------------|----------------|  
|`ref class`<br /><br /> `ref struct`|No|Declara una clase.|[Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`value class`<br /><br /> `value struct`|No|Declara una clase de valor.|[Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`interface class`<br /><br /> `interface struct`|No|Declara una interfaz.|[clase de interfaz](../windows/interface-class-cpp-component-extensions.md)|  
|`enum class`<br /><br /> `enum struct`|No|Declara una enumeración.|[enum class](../windows/enum-class-cpp-component-extensions.md)|  
|`property`|Sí|Declara una propiedad.|[propiedad](../windows/property-cpp-component-extensions.md)|  
|`delegate`|Sí|Declara un delegado.|[delegado](../windows/delegate-cpp-component-extensions.md)|  
|`event`|Sí|Declara un evento.|[event](../windows/event-cpp-component-extensions.md)|  
  
## Especificadores de invalidación  
 Puede usar las palabras clave siguientes para calificar el comportamiento de invalidación de la derivación.  Aunque la palabra clave `new` no es una extensión de C\+\+, se muestra aquí porque se puede usar en un contexto adicional.  Algunos especificadores también son válidos para la programación nativa.  Para obtener más información, vea [Cómo: Declarar especificadores de invalidación en las compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
|Palabra clave|Contextual|Finalidad|Referencia|  
|-------------------|----------------|---------------|----------------|  
|`abstract`|Sí|Indica que las funciones o las clases son abstractas.|[abstractas](../windows/abstract-cpp-component-extensions.md)|  
|`new`|No|Indica que una función no es una invalidación de una versión de la clase base.|[new \(nueva ranura en vtable\)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|  
|`override`|Sí|Indica que un método debe ser una invalidación de una versión de la clase base.|[override](../windows/override-cpp-component-extensions.md)|  
|`sealed`|Sí|Evita que las clases se usen como clases base.|[sellado](../windows/sealed-cpp-component-extensions.md)|  
  
## Palabras clave para genéricos  
 Las palabras clave siguientes se han agregado para admitir tipos genéricos.  Para obtener más información, vea [Genéricos](../windows/generics-cpp-component-extensions.md).  
  
|Palabra clave|Contextual|Propósito|  
|-------------------|----------------|---------------|  
|`generic`|No|Declara un tipo genérico.|  
|`where`|Sí|Especifica las restricciones que se aplican a un parámetro de tipo genérico.|  
  
## Palabras clave varias  
 Las palabras clave siguientes se han agregado a las extensiones de C\+\+.  
  
|Palabra clave|Contextual|Finalidad|Referencia|  
|-------------------|----------------|---------------|----------------|  
|`finally`|Sí|Indica el comportamiento predeterminado de los controles de excepciones.|[Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)|  
|`for each, in`|No|Enumera los elementos de una colección.|[for each, in](../dotnet/for-each-in.md)|  
|`gcnew`|No|Asigna tipos en el montón de recolección de elementos no utilizados.  Úselo en lugar de `new` y `delete`.|[ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`ref new`|Sí|Asigna un tipo [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  Úselo en lugar de `new` y `delete`.|[ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`initonly`|Sí|Indica que un miembro solo se puede inicializar en la declaración o en un constructor estático.|[initonly](../dotnet/initonly-cpp-cli.md)|  
|`literal`|Sí|Crea una variable literal.|[literal](../windows/literal-cpp-component-extensions.md)|  
|`nullptr`|No|Indica que un identificador o un puntero no señalan un objeto.|[nullptr](../windows/nullptr-cpp-component-extensions.md)|  
  
## Construcciones de plantilla  
 Las construcciones de lenguaje siguientes se implementan como plantillas, en lugar de como palabras clave.  Si especifica la opción del compilador **\/ZW**, se definen en el espacio de nombres `lang`.  Si especifica la opción del compilador **\/clr**, se definen en el espacio de nombres `cli`.  
  
|Palabra clave|Finalidad|Referencia|  
|-------------------|---------------|----------------|  
|`array`|Declara una matriz.|[Matrices](../windows/arrays-cpp-component-extensions.md)|  
|`interior_ptr`|\(solo CLR\) Apunta a los datos de un tipo de referencia.|[interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)|  
|`pin_ptr`|\(solo CLR\) Apunta a los tipos de referencia CLR para suprimir temporalmente el sistema de recolección de elementos no utilizados.|[pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md)|  
|`safe_cast`|Determina y ejecuta el método óptimo de conversión para un tipo de runtime.|[safe\_cast](../windows/safe-cast-cpp-component-extensions.md)|  
|`typeid`|\(solo CLR\) Recupera un objeto <xref:System.Type?displayProperty=fullName> que describe el tipo o el objeto especificado.|[typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md)|  
  
## Declaradores  
 Los declaradores de tipo siguientes indican al runtime que debe administrar automáticamente la duración y eliminación de los objetos asignados.  
  
|Operador|Finalidad|Referencia|  
|--------------|---------------|----------------|  
|`^`|Declara un identificador a un objeto; es decir, un puntero a un objeto [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] o CLR que se elimina automáticamente cuando ya no se usa.|[Identificador a un operador de objeto \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|  
|`%`|Declara una referencia de seguimiento; es decir, una referencia a un objeto [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] o CLR que se elimina automáticamente cuando ya no se usa.|[Operador de referencia de seguimiento](../windows/tracking-reference-operator-cpp-component-extensions.md)|  
  
## Construcciones adicionales y temas relacionados  
 En esta sección se muestran construcciones de programación adicionales y temas que pertenecen a CLR.  
  
|Tema|Descripción|  
|----------|-----------------|  
|[\_\_identifier \(C\+\+\/CLI\)](../windows/identifier-cpp-cli.md)|\([!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y CLR\) Habilita el uso de palabras clave como identificadores.|  
|[Listas de argumentos de variables \(...\) \(C\+\+\/CLI\)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|\([!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y CLR\) Permite que una función tome un número variable de argumentos.|  
|[.Equivalentes de .NET Framework para tipos nativos de C\+\+](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Enumera los tipos CLR que se usan en lugar de los tipos enteros de C\+\+.|  
|Modificador `__declspec` de [appdomain](../cpp/appdomain.md)|El modificador `__declspec` que requiere la existencia de variables static y globales por appdomain.|  
|[Conversiones de estilo C con \/clr \(C\+\+\/CLI\)](../windows/c-style-casts-with-clr-cpp-cli.md)|Describe cómo se interpretan las conversiones de tipo C.|  
|Convención de llamada [\_\_clrcall](../cpp/clrcall.md)|Indica la convención de llamada conforme a CLR.|  
|`__cplusplus_cli`|[Macros predefinidas](../preprocessor/predefined-macros.md)|  
|[Custom Attributes](../windows/custom-attributes-cpp.md)|Describe cómo definir sus propios atributos de CLR.|  
|[Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)|Proporciona información general sobre el control de excepciones.|  
|[Invalidaciones explícitas](../windows/explicit-overrides-cpp-component-extensions.md)|Muestra cómo las funciones miembro pueden invalidar miembros arbitrarios.|  
|[Ensamblados de confianza \(C\+\+\)](../dotnet/friend-assemblies-cpp.md)|Explica cómo un ensamblado de cliente puede tener acceso a todos los tipos de un componente de ensamblado.|  
|[Conversión boxing](../windows/boxing-cpp-component-extensions.md)|Muestra las condiciones en las que a los tipos de valores se les aplica la conversión boxing.|  
|[Compatibilidad de compilador para type traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|Explica cómo detectar características de tipos en tiempo de compilación.|  
|Pragmas [managed, unmanaged](../preprocessor/managed-unmanaged.md)|Muestra cómo las funciones administradas y no administradas pueden coexistir en el mismo módulo.|  
|Modificador `__declspec` de [proceso](../cpp/process.md)|El modificador `__declspec` que requiere la existencia de variables static y globales por proceso.|  
|[Reflexión](../dotnet/reflection-cpp-cli.md)|Muestra la versión de CLR de la información de tipo en tiempo de ejecución.|  
|[Cadena](../windows/string-cpp-component-extensions.md)|Describe la conversión del compilador de literales de cadena a <xref:System.String>.|  
|[Reenvío de tipos \(C\+\+\/CLI\)](../windows/type-forwarding-cpp-cli.md)|Habilita el movimiento de un tipo en un ensamblado de envío a otro ensamblado de modo que no es necesario volver a compilar el código de cliente.|  
|[Atributos definidos por el usuario](../windows/user-defined-attributes-cpp-component-extensions.md)|Muestra atributos definidos por el usuario.|  
|[\#using \(Directiva\)](../preprocessor/hash-using-directive-cpp.md)|Importa ensamblados externos.|  
|[Documentación de XML](../ide/xml-documentation-visual-cpp.md)|Explica la documentación de código basada en XML mediante el uso de [\/doc \(procesar comentarios de documentación\)](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
  
## Vea también  
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)