---
title: Extensiones de componentes de .NET y UWP | Documentos de Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45f83fbaaa867e2f58e329d8531259fa3751a521
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328420"
---
# <a name="component-extensions-for-net-and-uwp"></a>Extensiones de componentes de .NET y UWP

El estándar de C++ permite que los proveedores de compiladores proporcionar las extensiones no estándares del lenguaje. Microsoft proporciona extensiones para ayudarle a conectar C++ nativo a código que se ejecuta en .NET Framework o la plataforma Universal de Windows (UWP). Se llama a las extensiones de .NET C++ / c++ / CLI y generan código que se ejecuta en .NET administra el entorno de ejecución que se llama a Common Language Runtime (CLR). Las extensiones UWP se llaman C++ / c++ / CX y generan código máquina nativo.

> [!NOTE]
> Para las aplicaciones nuevas, se recomienda usar C++ / c++ / WinRT en lugar de C++ / c++ / CX. C++ / c++ / WinRT es una nueva, el estándar C ++ 17 proyección del lenguaje para Windows Runtime APIs. Se seguirá admitiendo C++ / c++ / CX y WRL, pero se recomienda encarecidamente que utilicen las nuevas aplicaciones C++ / c++ / WinRT. Para obtener más información, consulte [C++ / c++ / WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

### <a name="two-runtimes-one-set-of-extensions"></a>Dos runtime, un conjunto de extensiones

C++ / c++ / CLI amplía el estándar de C++ de ANSI/ISO y se define en Ecma C++ / c++ / CLI estándar. Para obtener más información, consulte [programación de .NET con C++ / c++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

C++ / c++ / extensiones CX son un subconjunto de C / c++ / CLI. Aunque la sintaxis de extensión es idéntica en la mayoría de los casos, el código que se genera depende de si se especifica la `/ZW` que tengan como destino UWP, opción del compilador o el `/clr` opción tienen como destino .NET. Estos modificadores se establecen automáticamente cuando se usa Visual Studio para crear un proyecto.

## <a name="data-type-keywords"></a>Palabras clave de tipo de datos

Las extensiones de lenguaje incluyen *agregar palabras clave*, que constan de dos tokens separados por espacios en blanco. Los tokens pueden tener un significado cuando se usan por separado, y otro significado cuando se usan juntos. Por ejemplo, la palabra “ref” es un identificador normal, y la palabra “clase” es una palabra clave que declara una clase nativa. Pero cuando estas palabras se combinan para formar **clase ref**, la palabra clave agregada resultante declara una entidad que se conoce como un *clase en tiempo de ejecución*.

Las extensiones también incluyen *contextual* palabras clave. Una palabra clave se trata como contextual en función del tipo de instrucción que la contenga, y de su posición en esa instrucción. Por ejemplo, el token “property” puede ser un identificador, o puede declarar una clase especial de miembro de clase pública.

En la tabla siguiente se enumeran las palabras clave en la extensión del lenguaje C++.

|Palabra clave|Contextual|Propósito|Referencia|
|-------------|-----------------------|-------------|---------------|
|**clase ref**<br /><br /> **struct ref**|No|Declara una clase.|[Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)|
|**clase de valor**<br /><br /> **struct de valor**|No|Declara una clase de valor.|[Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)|
|**clase de interfaz**<br /><br /> **struct de interfaz**|No|Declara una interfaz.|[clase de interfaz](../windows/interface-class-cpp-component-extensions.md)|
|**clase Enum**<br /><br /> **enum struct**|No|Declara una enumeración.|[clase Enum](../windows/enum-class-cpp-component-extensions.md)|
|**propiedad**|Sí|Declara una propiedad.|[propiedad](../windows/property-cpp-component-extensions.md)|
|**delegate**|Sí|Declara un delegado.|[delegado (C++ / c++ / CLI y c++ / CX)](../windows/delegate-cpp-component-extensions.md)|
|**event**|Sí|Declara un evento.|[event](../windows/event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>Especificadores de invalidación

Puede usar las palabras clave siguientes para calificar el comportamiento de invalidación de la derivación. Aunque el **nuevo** palabra clave no es una extensión de C++, se muestra aquí porque se puede utilizar en un contexto adicional. Algunos especificadores también son válidos para la programación nativa. Para obtener más información, consulte [Cómo: declarar especificadores de reemplazo en compilaciones nativas (C++ / c++ / CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

|Palabra clave|Contextual|Propósito|Referencia|
|-------------|-----------------------|-------------|---------------|
|**abstract**|Sí|Indica que las funciones o las clases son abstractas.|[abstract](../windows/abstract-cpp-component-extensions.md)|
|**new**|No|Indica que una función no es una invalidación de una versión de la clase base.|[New (nueva ranura en vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|Sí|Indica que un método debe ser una invalidación de una versión de la clase base.|[override](../windows/override-cpp-component-extensions.md)|
|**sealed**|Sí|Evita que las clases se usen como clases base.|[sealed](../windows/sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>Palabras clave para genéricos

Las palabras clave siguientes se han agregado para admitir tipos genéricos. Para más información, vea [Genéricos](../windows/generics-cpp-component-extensions.md).

|Palabra clave|Contextual|Propósito|
|-------------|-----------------------|-------------|
|**Genérico**|No|Declara un tipo genérico.|
|**where**|Sí|Especifica las restricciones que se aplican a un parámetro de tipo genérico.|

## <a name="miscellaneous-keywords"></a>Palabras clave varias

Las palabras clave siguientes se han agregado a las extensiones de C++.

|Palabra clave|Contextual|Propósito|Referencia|
|-------------|-----------------------|-------------|---------------|
|**finally**|Sí|Indica el comportamiento predeterminado de los controles de excepciones.|[Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)|
|**for each, in**|No|Enumera los elementos de una colección.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|No|Asigna tipos en el montón de recolección de elementos no utilizados. Use en lugar de **nueva** y **eliminar**.|[ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**referencia nuevos**|Sí|Asigna un tipo en tiempo de ejecución de Windows. Use en lugar de **nueva** y **eliminar**.|[ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|Sí|Indica que un miembro solo se puede inicializar en la declaración o en un constructor estático.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**literal**|Sí|Crea una variable literal.|[literal](../windows/literal-cpp-component-extensions.md)|
|**nullptr**|No|Indica que un identificador o un puntero no señalan un objeto.|[nullptr](../windows/nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>Construcciones de plantilla

Las construcciones de lenguaje siguientes se implementan como plantillas, en lugar de como palabras clave. Si especifica la opción del compilador `/ZW`, se definen en el espacio de nombres `lang`. Si especifica la opción del compilador `/clr`, se definen en el espacio de nombres `cli`.

|Palabra clave|Propósito|Referencia|
|-------------|-------------|---------------|
|**array**|Declara una matriz.|[Matrices](../windows/arrays-cpp-component-extensions.md)|
|**interior_ptr**|(solo CLR) Apunta a los datos de un tipo de referencia.|[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)|
|**pin_ptr**|(solo CLR) Apunta a los tipos de referencia CLR para suprimir temporalmente el sistema de recolección de elementos no utilizados.|[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)|
|**safe_cast**|Determina y ejecuta el método óptimo de conversión para un tipo de runtime.|[safe_cast](../windows/safe-cast-cpp-component-extensions.md)|
|**typeid**|(solo CLR) Recupera un objeto <xref:System.Type?displayProperty=fullName> que describe el tipo o el objeto especificado.|[typeid](../windows/typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>Declaradores

Los declaradores de tipo siguientes indican al runtime que debe administrar automáticamente la duración y eliminación de los objetos asignados.

|Operador|Propósito|Referencia|
|--------------|-------------|---------------|
|`^`|Declara un identificador a un objeto; es decir, un puntero a un objeto en tiempo de ejecución de Windows o CLR que se elimina automáticamente cuando ya no es utilizable.|[Identificador de operador de objeto (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|Declara una referencia de seguimiento; es decir, una referencia a un objeto en tiempo de ejecución de Windows o CLR que se elimina automáticamente cuando ya no es utilizable.|[Operador de referencia de seguimiento](../windows/tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>Construcciones adicionales y temas relacionados

En esta sección se muestran construcciones de programación adicionales y temas que pertenecen a CLR.

|Tema|Descripción|
|-----------|-----------------|
|[__identifier (C++/CLI)](../windows/identifier-cpp-cli.md)|(Windows en tiempo de ejecución y CLR) Habilita el uso de palabras clave como identificadores.|
|[Listas de argumentos de variables (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows en tiempo de ejecución y CLR) Permite que una función tomar un número variable de argumentos.|
|[Equivalentes de .NET Framework para tipos nativos de C++ (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Enumera los tipos CLR que se usan en lugar de los tipos enteros de C++.|
|[AppDomain](../cpp/appdomain.md) **__declspec** modificador|**__declspec** modificador que requiere la existen de variables static y globales por appdomain.|
|[Conversiones de estilo C con /clr (C++ / c++ / CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)|Describe cómo se interpretan las conversiones de tipo C.|
|[__clrcall](../cpp/clrcall.md) convención de llamada|Indica la convención de llamada conforme a CLR.|
|`__cplusplus_cli`|[Macros predefinidas](../preprocessor/predefined-macros.md)|
|[Atributos personalizados](../windows/custom-attributes-cpp.md)|Describe cómo definir sus propios atributos de CLR.|
|[Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)|Proporciona información general sobre el control de excepciones.|
|[Invalidaciones explícitas](../windows/explicit-overrides-cpp-component-extensions.md)|Muestra cómo las funciones miembro pueden invalidar miembros arbitrarios.|
|[Ensamblados de confianza (C++)](../dotnet/friend-assemblies-cpp.md)|Explica cómo un ensamblado de cliente puede tener acceso a todos los tipos de un componente de ensamblado.|
|[Conversión boxing](../windows/boxing-cpp-component-extensions.md)|Muestra las condiciones en las que a los tipos de valores se les aplica la conversión boxing.|
|[Compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|Explica cómo detectar características de tipos en tiempo de compilación.|
|[Managed, unmanaged](../preprocessor/managed-unmanaged.md) directivas pragma|Muestra cómo las funciones administradas y no administradas pueden coexistir en el mismo módulo.|
|[proceso](../cpp/process.md) **__declspec** modificador|**__declspec** modificador que requiere la existen de variables static y globales por proceso.|
|[Reflexión (C++-CLI)](../dotnet/reflection-cpp-cli.md)|Muestra la versión de CLR de la información de tipo en tiempo de ejecución.|
|[String](../windows/string-cpp-component-extensions.md)|Describe la conversión del compilador de literales de cadena a <xref:System.String>.|
|[Reenvío de tipos (C++/CLI)](../windows/type-forwarding-cpp-cli.md)|Habilita el movimiento de un tipo en un ensamblado de envío a otro ensamblado de modo que no es necesario volver a compilar el código de cliente.|
|[Atributos definidos por el usuario](../windows/user-defined-attributes-cpp-component-extensions.md)|Muestra atributos definidos por el usuario.|
|[#using (directiva)](../preprocessor/hash-using-directive-cpp.md)|Importa ensamblados externos.|
|[Documentación de XML](../ide/xml-documentation-visual-cpp.md)|Explica la documentación de código basado en XML mediante el uso de [/doc (procesar comentarios de documentación) (C/C ++)](../build/reference/doc-process-documentation-comments-c-cpp.md)|

## <a name="see-also"></a>Vea también

[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)