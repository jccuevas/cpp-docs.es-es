---
title: Sistema de tipos (C++/CX)
ms.date: 02/03/2017
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
ms.openlocfilehash: bc45a835e37ff4e3ea239d253078bf50eab1b2ff
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740899"
---
# <a name="type-system-ccx"></a>Sistema de tipos (C++/CX)

Mediante el uso de la arquitectura de Windows Runtime, C++puede usar/cx, Visual Basic C# , visual y JavaScript para escribir aplicaciones y componentes que acceden directamente a la API de Windows e interoperan con otras aplicaciones y componentes de Windows Runtime. Plataforma universal de Windows las aplicaciones que se escriben en se compilan en C++ código nativo que se ejecuta directamente en la CPU. Plataforma universal de Windows las aplicaciones escritas en C# o Visual Basic compilar en lenguaje intermedio de Microsoft (MSIL) y ejecutarse en el Common Language Runtime (CLR). Plataforma universal de Windows las aplicaciones escritas en JavaScript se ejecutan en un entorno en tiempo de ejecución. Los componentes del sistema operativo Windows Runtime se escriben C++ y se ejecutan como código nativo. Todos estos componentes y aplicaciones Plataforma universal de Windows se comunican directamente a través de la interfaz binaria de aplicación Windows Runtime (ABI).

Para habilitar la compatibilidad con la Windows Runtime en una C++ expresión moderna, Microsoft creó C++el/CX. C++/CX proporciona implementaciones y tipos base integrados de tipos de Windows Runtime fundamentales que permiten C++ que las aplicaciones y los componentes se comuniquen a través de la ABI con aplicaciones escritas en otros lenguajes. Puede usar cualquier Windows Runtime tipo o crear clases, Structs, interfaces y otros tipos definidos por el usuario que se puedan usar en otras aplicaciones y componentes de Plataforma universal de Windows. una aplicación Plataforma universal de Windows escrita en C++/CX también puede usar clases y Structs regulares C++ siempre y cuando no tengan accesibilidad pública.

Si quiere ver una discusión en profundidad sobre la proyección del lenguaje C++/CX y cómo funciona tras los bastidores, consulte estas publicaciones de blogs:

1. [C++/CX, parte 0 \[de\]n: Una introducción](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)

1. [C++/CX, parte 1 \[de\]n: Una clase simple](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)

1. [C++/CX, parte 2 \[de\]n: Tipos que desgasten los sombreros](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)

1. [C++/CX, parte 3 \[de\]n: En construcción](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)

1. [C++/CX, parte 4 \[de\]n: Funciones miembro estáticas](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)

## <a name="windows-metadata-winmd-files"></a>Archivos de metadatos de Windows (.winmd)

Al compilar una aplicación Plataforma universal de Windows escrita en C++, el compilador genera el ejecutable en código máquina nativo y también genera un archivo de metadatos de Windows (. winmd) independiente que contiene descripciones del Windows Runtime público tipos, que incluyen clases, estructuras, enumeraciones, interfaces, interfaces parametrizadas y delegados. El formato de los metadatos se parece al formato que se utiliza en los ensamblados de .NET Framework.  En un componente de C++, el archivo .winmd solo contiene metadatos; el código ejecutable reside en un archivo independiente. Este es el caso de los componentes de Windows Runtime que se incluyen con Windows. El nombre de archivo WinMD tiene que coincidir o ser un prefijo del espacio de nombres raíz en el código fuente. (Para los lenguajes de .NET Framework, el archivo de .winmd contiene el código y los metadatos, como un ensamblado de .NET Framework).

Los metadatos del archivo de .winmd representan la superficie publicada de tu código. Los tipos publicados son visibles para otras plataformas universales de Windows, independientemente del idioma en el que se escriban esas otras aplicaciones. Por lo tanto, los metadatos, o el código publicado, solo pueden contener tipos especificados por el sistema de tipos de Windows Runtime. Las construcciones de lenguaje específicas de C++, como clases, matrices, plantillas o contenedores STL normales, no se pueden publicar en los metadatos porque una aplicación cliente de JavaScript o de C# no sabría lo que debería hacer con ellas.

Que un tipo o un método estén visibles en los metadatos depende de los modificadores de accesibilidad que se les aplique. Para que esté visible, un tipo se debe declarar en un espacio de nombres y como público. Una clase ref pública se permite como tipo del asistente interno en tu código; simplemente no está visible en los metadatos. Incluso en una clase ref pública, no todos los miembros están visibles necesariamente. En la tabla siguiente se muestra la C++ relación entre los especificadores de acceso en una clase Ref pública y Windows Runtime la visibilidad de los metadatos:

|||
|-|-|
|**Publicado en metadatos**|**No publicado en metadatos**|
|public|private|
|protected|internal|
|público protegido|privado protegido|

Puedes utilizar el **Explorador de objetos** para ver el contenido de los archivos .winmd. Los componentes de Windows Runtime que se incluyen en Windows están en el archivo Windows. winmd. El archivo default. winmd contiene los tipos fundamentales que se usan en C++/CX y Platform. winmd contiene tipos adicionales del espacio de nombres de la plataforma. De forma predeterminada, estos tres archivos. winmd se incluyen en C++ todos los proyectos de plataforma universal de Windows aplicaciones.

> [!TIP]
> Los tipos de [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) no aparecen en el archivo .winmd porque no son públicos. Son implementaciones específicas de C++ privadas de las interfaces que se definen en `Windows::Foundation::Collections`. Una aplicación Windows Runtime escrita en JavaScript o C# no sabe qué es una [clase Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) , pero puede consumir un. `Windows::Foundation::Collections::IVector` Los tipos de `Platform::Collections` se definen en collection.h.

## <a name="windows-runtime-type-system-in-ccx"></a>Windows Runtime sistema de tipos C++en/CX

En las secciones siguientes se describen las características principales del sistema de tipos de Windows Runtime y cómo se C++admiten en/CX.

### <a name="namespaces"></a>Espacios de nombres

Todos los tipos de Windows Runtime se deben declarar dentro de un espacio de nombres; la propia API de Windows se organiza mediante espacios de nombres. Un archivo .winmd debe tener el mismo nombre que el espacio de nombres de la raíz. Por ejemplo, se pueden crear instancias de una clase denominada A.B.C.MyClass solo si está definida en un archivo de metadatos denominado A.winmd, A.B.winmd o A.B.C.winmd. El nombre de la DLL no tiene que coincidir con el nombre del archivo .winmd.

La propia API de Windows se ha reinventado como una biblioteca de clases correctamente factorizada que se organiza mediante espacios de nombres.  Todos los componentes de Windows Runtime se declaran en los espacios de nombres Windows. *.

Para más información, vea [espacios de nombres y visibilidad de tipos](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="fundamental-types"></a>Tipos fundamentales

El Windows Runtime define los siguientes tipos fundamentales: UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, single, Double, Char16, Boolean y String. C++/CX admite los tipos numéricos fundamentales en su espacio de nombres predeterminado como UInt16, UInt32, UInt64, Int16, Int32, Int64, float32, float64 y char16. Boolean y String también se definen en el espacio de nombres Platform.

C++/CX también define Uint8, equivalente a `unsigned char`, que no se admite en el Windows Runtime y no se puede usar en las API públicas.

Un tipo fundamental puede convertirse en un tipo que acepte valores NULL incluyéndolo en una [interfaz Platform::IBox](../cppcx/platform-ibox-interface.md) . Para obtener más información, consulta [Clases y structs de valor](../cppcx/value-classes-and-structs-c-cx.md).

Para obtener más información sobre los tipos fundamentales, consulta [Tipos fundamentales](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>Cadenas

Una cadena Windows Runtime es una secuencia inmutable de caracteres Unicode de 16 bits. Una cadena de Windows Runtime se proyecta `Platform::String^`como. Esta clase proporciona métodos para la construcción, manipulación y conversión de cadenas a un tipo `wchar_t`y desde dicho tipo.

Para obtener más información, consulta [Cadenas](../cppcx/strings-c-cx.md).

### <a name="arrays"></a>Matrices

El Windows Runtime admite Matrices unidimensionales de cualquier tipo. No se admiten matrices de matrices.  En C++/CX, las matrices de Windows Runtime se proyectan como la [clase Platform:: Array](../cppcx/platform-array-class.md).

Para obtener más información, consulte [array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="ref-classes-and-structs"></a>Clases ref y structs ref

Una clase de Windows Runtime se proyecta C++en/CX como una clase Ref o un struct Ref, ya que se copian por referencia. La administración de memoria para clases ref y structs ref se controlan de forma transparente mediante el recuento de referencias. Cuando la última referencia a un objeto sale del ámbito, el objeto se destruye. Una clase ref y un struct ref pueden:

- Contener como miembros constructores, métodos, propiedades y eventos. Estos miembros pueden tener accesibilidad pública, privada, protegida o interna.

- Contener definiciones de clases, structs o enumeraciones de tipo anidado privado.

- Heredar directamente de una clase base e implementar cualquier número de interfaces. Todas las clases ref se pueden convertir implícitamente a [Platform::Object Class](../cppcx/platform-object-class.md) y pueden invalidar sus métodos virtuales como [Object::ToString](../cppcx/platform-object-class.md#tostring).

Una clase ref que tenga un constructor público se debe declarar como sellada, para evitar la derivación adicional.

Para obtener más información, consulta [Clases ref y structs ref](../cppcx/ref-classes-and-structs-c-cx.md)

### <a name="value-classes-and-structs"></a>Clases y structs de valor

Una clase de valor o un struct de valor representan una estructura de datos básicos y solo contienen campos, que pueden ser clases de valor, structs de valor o `Platform::String^`de tipo.  Los structs de valor y las clases de valor se copian por valor.

Un struct de valor se puede convertir en un struct que acepte valores NULL incluyéndolo en una interfaz IBox.

Para obtener más información, consulta [Clases y structs de valor](../cppcx/value-classes-and-structs-c-cx.md).

### <a name="partial-classes"></a>Clases parciales

La característica de clases parciales permite definir una clase en varios archivos. Se utiliza principalmente para permitir a las herramientas de generación de código como el editor de XAML modificar un archivo sin tocar el archivo que estás editando.

Para obtener más información, consulta [Clases parciales](../cppcx/partial-classes-c-cx.md)

### <a name="properties"></a>Properties (Propiedades)

Una propiedad es un miembro de datos público de cualquier tipo de Windows Runtime y se implementa como un par de métodos Get/Set. El código de cliente tiene acceso a una propiedad como si fuera un campo público. Una propiedad que no requiere código de tipo get o set personalizado se conoce como *propiedad trivial* y se puede declarar sin métodos de tipo get o set explícitos.

Para obtener más información, consulta [Propiedades](../cppcx/properties-c-cx.md).

### <a name="windows-runtime-collections-in-ccx"></a>Windows Runtime colecciones en C++/CX

El Windows Runtime define un conjunto de interfaces para los tipos de colección que cada lenguaje implementa de manera propia. C++/CX proporciona implementaciones en la clase [Platform:: Collections:: Vector (clase](../cppcx/platform-collections-vector-class.md)), [Platform:: Collections:: Map Class](../cppcx/platform-collections-map-class.md)y otros tipos de colección concretos relacionados, que son compatibles con sus homólogos de la biblioteca de plantillas estándar (STL).

Para obtener más información, vea [colecciones](../cppcx/collections-c-cx.md).

### <a name="template-ref-classes"></a>Clases ref de plantilla

Las clases privadas y las clases ref internas se pueden convertir en plantillas y personalizarse para usos concretos.

Para obtener más información, consulta [Clases ref de plantilla](../cppcx/template-ref-classes-c-cx.md).

### <a name="interfaces"></a>Interfaces

Una interfaz de Windows Runtime define un conjunto de propiedades, métodos y eventos públicos que una clase Ref o un struct Ref deben implementar si hereda de la interfaz.

Para más información, vea [Interfaces](../cppcx/interfaces-c-cx.md).

### <a name="enums"></a>Enumeraciones

Una clase de enumeración en Windows Runtime se parece a una enumeración con ámbito en C++. El tipo subyacente es int32, a menos que se aplique el atributo [Flags]; en ese caso, el tipo subyacente es uint32.

Para obtener más información, consulta [Enumeraciones](../cppcx/enums-c-cx.md).

### <a name="delegates"></a>Delegados

Un delegado en el Windows Runtime es análogo a un objeto STD:: function en C++. Es un tipo especial de clase ref que se utiliza para invocar funciones proporcionadas por el cliente que tienen firmas compatibles.  Los delegados se utilizan normalmente en el Windows Runtime como el tipo de un evento.

Para obtener más información, vea [Delegados (Guía de programación de C#)](../cppcx/delegates-c-cx.md).

### <a name="exceptions"></a>Excepciones

En C++/CX, puedes detectar tipos de excepción personalizados, tipos [std::exception](../standard-library/exception-class.md) y tipos [Platform::Exception](../cppcx/platform-exception-class.md) .

Para obtener más información, consulta [Excepciones](../cppcx/exceptions-c-cx.md).

### <a name="events"></a>Events

Un evento es un miembro público en una clase ref o un struct ref cuyo tipo es un tipo delegado. Un evento solo puede ser invocado, es decir desencadenado, por la clase propietaria. Sin embargo, el código de cliente puede proporcionar sus propias funciones, que se denominan controladores de eventos y se invocan cuando la clase propietaria desencadena el evento.

Para obtener más información, consulta [Eventos](../cppcx/events-c-cx.md).

### <a name="casting"></a>Conversión

C++/CX admite los operadores de conversión estándar de C++ [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md)y [reinterpret_cast](../cpp/reinterpret-cast-operator.md), y también el operador **safe_cast** que es específico de C++/CX.

Para obtener más información, consulta [Conversión](../cppcx/casting-c-cx.md).

### <a name="boxing"></a>Boxing

Una variable a la que se le ha aplicado una conversión boxing es un tipo de valor incluido en un tipo de referencia usado en situaciones donde se es necesaria una semántica de referencia.

Para obtener más información, consulta [Boxing](../cppcx/boxing-c-cx.md).

### <a name="attributes"></a>Atributos

Un atributo es un valor de metadatos que se puede aplicar a cualquier Windows Runtime tipo o miembro de tipo y se puede inspeccionar en tiempo de ejecución. El Windows Runtime define un conjunto de atributos comunes en el `Windows::Foundation::Metadata` espacio de nombres. Los atributos definidos por el usuario en interfaces públicas no se admiten en Windows Runtime en esta versión.

## <a name="api-deprecation"></a>Marcar la API como en desuso

Describe cómo marcar las API públicas como desusadas utilizando el mismo atributo que usan los tipos de sistema Windows Runtime.

Para obtener más información, vea [desuso de tipos y miembros](../cppcx/deprecating-types-and-members-c-cx.md).

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
