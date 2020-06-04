---
title: Extensiones de componentes de .NET y UWP
ms.date: 10/12/2018
ms.topic: overview
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: 6b3add1c0de8aa1f8ec66e8d220443c4a0efd704
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172470"
---
# <a name="component-extensions-for-net-and-uwp"></a>Extensiones de componentes de .NET y UWP

El estándar C++ permite a los proveedores de compiladores proporcionar extensiones no estándar al lenguaje. Microsoft proporciona extensiones para ayudar a conectar código C++ nativo a código que se ejecuta en .NET Framework o la Plataforma universal de Windows (UWP). A las extensiones .NET se les llama C++/CLI y producen código que se ejecuta en el entorno de ejecución administrado de .NET denominado Common Language Runtime (CLR). A las extensiones UWP se les llama C++/CX y producen código máquina nativo.

> [!NOTE]
> Para nuevas aplicaciones, recomendamos usar C++/WinRT en lugar de C++/CX. C++/WinRT es una proyección de lenguaje C++17 nueva y estándar para las API de Windows Runtime. Seguiremos admitiendo C++/CX y WRL, pero recomendamos encarecidamente que las nuevas aplicaciones usen C++/WinRT. Para obtener más información, consulte [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

### <a name="two-runtimes-one-set-of-extensions"></a>Dos runtime, un conjunto de extensiones

C++/CLI extiende el estándar C++ de ANSI/ISO y se define en la norma ECMA de C++/CLI. Par obtener más información, consulte el artículo sobre [la programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Las extensiones para C++/CX son un subconjunto de C++/CLI. Aunque la sintaxis de extensiones es idéntica en la mayoría de los casos, el código que se genera depende de si especifica la opción del compilador `/ZW` para establecer UWP como destino o la opción `/clr` para establecer .NET como destino. Estos modificadores se establecen automáticamente cuando se usa Visual Studio para crear un proyecto.

## <a name="data-type-keywords"></a>Palabras clave de tipo de datos

Las extensiones de lenguaje incluyen *palabras clave agregadas*, que constan de dos tokens separados por espacios en blanco. Los tokens pueden tener un significado cuando se usan por separado, y otro significado cuando se usan juntos. Por ejemplo, la palabra “ref” es un identificador normal, y la palabra “clase” es una palabra clave que declara una clase nativa. Pero cuando estas palabras se combinan para formar **ref class**, la palabra clave agregada resultante declara una entidad denominada *clase en tiempo de ejecución*.

Las extensiones también incluyen palabras clave *contextuales*. Una palabra clave se trata como contextual en función del tipo de instrucción que la contenga, y de su posición en esa instrucción. Por ejemplo, el token “property” puede ser un identificador, o puede declarar una clase especial de miembro de clase pública.

En la tabla siguiente se enumeran las palabras clave en la extensión del lenguaje C++.

|Palabra clave|Contextual|Propósito|Referencia|
|-------------|-----------------------|-------------|---------------|
|**ref class**<br /><br /> **ref struct**|No|Declara una clase.|[Clases y structs](classes-and-structs-cpp-component-extensions.md)|
|**value class**<br /><br /> **value struct**|No|Declara una clase de valor.|[Clases y structs](classes-and-structs-cpp-component-extensions.md)|
|**clase de interfaz**<br /><br /> **interface struct**|No|Declara una interfaz.|[clase de interfaz](interface-class-cpp-component-extensions.md)|
|**enum class**<br /><br /> **enum struct**|No|Declara una enumeración.|[enum class](enum-class-cpp-component-extensions.md)|
|**property**|Sí|Declara una propiedad.|[property](property-cpp-component-extensions.md)|
|**delegate**|Sí|Declara un delegado.|[delegate (C++/CLI y C++/CX)](delegate-cpp-component-extensions.md)|
|**event**|Sí|Declara un evento.|[event](event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>Especificadores de invalidación

Puede usar las palabras clave siguientes para calificar el comportamiento de invalidación de la derivación. Aunque la palabra clave **new** no es una extensión de C++, se muestra aquí porque se puede usar en un contexto adicional. Algunos especificadores también son válidos para la programación nativa. Para obtener más información, vea [Cómo: declarar especificadores de invalidación en compilaciones nativas (C++/CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

|Palabra clave|Contextual|Propósito|Referencia|
|-------------|-----------------------|-------------|---------------|
|**abstract**|Sí|Indica que las funciones o las clases son abstractas.|[abstract](abstract-cpp-component-extensions.md)|
|**nuevo**|No|Indica que una función no es una invalidación de una versión de la clase base.|[new (nueva ranura en vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|Sí|Indica que un método debe ser una invalidación de una versión de la clase base.|[override](override-cpp-component-extensions.md)|
|**sealed**|Sí|Evita que las clases se usen como clases base.|[sealed](sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>Palabras clave para genéricos

Las palabras clave siguientes se han agregado para admitir tipos genéricos. Para más información, vea [Genéricos](generics-cpp-component-extensions.md).

|Palabra clave|Contextual|Propósito|
|-------------|-----------------------|-------------|
|**generic**|No|Declara un tipo genérico.|
|**where**|Sí|Especifica las restricciones que se aplican a un parámetro de tipo genérico.|

## <a name="miscellaneous-keywords"></a>Palabras clave varias

Las palabras clave siguientes se han agregado a las extensiones de C++.

|Palabra clave|Contextual|Propósito|Referencia|
|-------------|-----------------------|-------------|---------------|
|**finally**|Sí|Indica el comportamiento predeterminado de los controles de excepciones.|[Control de excepciones](exception-handling-cpp-component-extensions.md)|
|**for each, in**|No|Enumera los elementos de una colección.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|No|Asigna tipos en el montón de recolección de elementos no utilizados. Úsela en lugar de **new** y **delete**.|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**ref new**|Sí|Asigna un tipo de Windows Runtime. Úsela en lugar de **new** y **delete**.|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|Sí|Indica que un miembro solo se puede inicializar en la declaración o en un constructor estático.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**literal**|Sí|Crea una variable literal.|[literal](literal-cpp-component-extensions.md)|
|**nullptr**|No|Indica que un identificador o un puntero no señalan un objeto.|[nullptr](nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>Construcciones de plantilla

Las construcciones de lenguaje siguientes se implementan como plantillas, en lugar de como palabras clave. Si especifica la opción del compilador `/ZW`, se definen en el espacio de nombres `lang`. Si especifica la opción del compilador `/clr`, se definen en el espacio de nombres `cli`.

|Palabra clave|Propósito|Referencia|
|-------------|-------------|---------------|
|**array**|Declara una matriz.|[Matrices](arrays-cpp-component-extensions.md)|
|**interior_ptr**|(solo CLR) Apunta a los datos de un tipo de referencia.|[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)|
|**pin_ptr**|(solo CLR) Apunta a los tipos de referencia CLR para suprimir temporalmente el sistema de recolección de elementos no utilizados.|[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)|
|**safe_cast**|Determina y ejecuta el método óptimo de conversión para un tipo de runtime.|[safe_cast](safe-cast-cpp-component-extensions.md)|
|**typeid**|(solo CLR) Recupera un objeto <xref:System.Type?displayProperty=fullName> que describe el tipo o el objeto especificado.|[typeid](typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>Declaradores

Los declaradores de tipo siguientes indican al runtime que debe administrar automáticamente la duración y eliminación de los objetos asignados.

|Operator|Propósito|Referencia|
|--------------|-------------|---------------|
|`^`|Declara un identificador a un objeto; es decir, un puntero a un objeto Windows Runtime o CLR que se elimina automáticamente cuando ya no se usa.|[Identificador a un operador de objeto (^)](handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|Declara una referencia de seguimiento; es decir, una referencia a un objeto Windows Runtime o CLR que se elimina automáticamente cuando ya no se usa.|[Operador de referencia de seguimiento](tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>Construcciones adicionales y temas relacionados

En esta sección se muestran construcciones de programación adicionales y temas que pertenecen a CLR.

|Tema|Descripción|
|-----------|-----------------|
|[__identifier (C++/CLI)](identifier-cpp-cli.md)|(Windows Runtime y CLR) Habilita el uso de palabras clave como identificadores.|
|[Listas de argumentos de variables (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows Runtime y CLR) Permite que una función tome un número variable de argumentos.|
|[Equivalentes de .NET Framework para tipos nativos de C++ (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Enumera los tipos CLR que se usan en lugar de los tipos enteros de C++.|
|[appdomain](../cpp/appdomain.md) **__declspec** modificador de AppDomain|Modificador **__declspec** que requiere la existencia de variables static y globales por appdomain.|
|[Conversiones de estilo C con /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)|Describe cómo se interpretan las conversiones de tipo C.|
|Convención de llamada [__clrcall](../cpp/clrcall.md)|Indica la convención de llamada conforme a CLR.|
|`__cplusplus_cli`|[Macros predefinidas](../preprocessor/predefined-macros.md)|
|[Atributos personalizados](user-defined-attributes-cpp-component-extensions.md)|Describe cómo definir sus propios atributos de CLR.|
|[Control de excepciones](exception-handling-cpp-component-extensions.md)|Proporciona información general sobre el control de excepciones.|
|[Invalidaciones explícitas](explicit-overrides-cpp-component-extensions.md)|Muestra cómo las funciones miembro pueden invalidar miembros arbitrarios.|
|[Ensamblados de confianza (C++)](../dotnet/friend-assemblies-cpp.md)|Explica cómo un ensamblado de cliente puede tener acceso a todos los tipos de un componente de ensamblado.|
|[Conversión boxing](boxing-cpp-component-extensions.md)|Muestra las condiciones en las que a los tipos de valores se les aplica la conversión boxing.|
|[Compatibilidad de compilador para type traits](compiler-support-for-type-traits-cpp-component-extensions.md)|Explica cómo detectar características de tipos en tiempo de compilación.|
|Pragmas [managed, unmanaged](../preprocessor/managed-unmanaged.md)|Muestra cómo las funciones administradas y no administradas pueden coexistir en el mismo módulo.|
|modificador **__declspec** de [proceso](../cpp/process.md)|Modificador **__declspec** que requiere la existencia de variables static y globales por proceso.|
|[Reflexión (C++-CLI)](../dotnet/reflection-cpp-cli.md)|Muestra la versión de CLR de la información de tipo en tiempo de ejecución.|
|[String](string-cpp-component-extensions.md)|Describe la conversión del compilador de literales de cadena a <xref:System.String>.|
|[Reenvío de tipos (C++/CLI)](type-forwarding-cpp-cli.md)|Habilita el movimiento de un tipo en un ensamblado de envío a otro ensamblado de modo que no es necesario volver a compilar el código de cliente.|
|[Atributos definidos por el usuario](user-defined-attributes-cpp-component-extensions.md)|Muestra atributos definidos por el usuario.|
|[#using (directiva)](../preprocessor/hash-using-directive-cpp.md)|Importa ensamblados externos.|
|[Documentación de XML](../build/reference/xml-documentation-visual-cpp.md)|Explica la documentación de código basada en XML mediante el uso de [/doc (procesar comentarios de documentación) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)|

## <a name="see-also"></a>Consulte también

[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)
