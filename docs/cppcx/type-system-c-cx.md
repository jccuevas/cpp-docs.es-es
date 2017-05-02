---
title: "Sistema de tipos (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
caps.latest.revision: 28
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 28
---
# Sistema de tipos (C++/CX)
Mediante la arquitectura de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], puedes utilizar [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)], Visual Basic, Visual C\# y JavaScript para escribir aplicaciones y componentes con acceso directo a la API de Windows e interactuar con otras aplicaciones y componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. Las aplicaciones [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] escritas en C\+\+ se compilan en código nativo que se ejecuta directamente en la CPU. Las aplicaciones de[!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] escritas en C\# o en Visual Basic se compilan en lenguaje intermedio de Microsoft \(MSIL\) y se ejecutan en Common Language Runtime \(CLR\). Las aplicaciones de[!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] escritas en JavaScript se ejecutan en un entorno en tiempo de ejecución. Los propios componentes del sistema operativo [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] se escriben en C\+\+ y se ejecutan como código nativo. Todos estos componentes y aplicaciones de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] se comunican directamente a través de la interfaz binaria de aplicación \(ABI\) de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
 Para habilitar la compatibilidad con [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] en una locución de C\+\+ moderno, Microsoft ha creado [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\).[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] proporciona implementaciones y tipos base integrados de tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] fundamentales que permiten que las aplicaciones y los componentes de C\+\+ se comuniquen a través de ABI con aplicaciones escritas en otros lenguajes. Puedes utilizar cualquier tipo de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] o crear clases, structs, interfaces y otros tipos definidos por el usuario que se pueden usar en otras aplicaciones y componentes de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]. Una aplicación de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] escrita en [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] también puede utilizar clases y structs de C\+\+ normal mientras no tengan accesibilidad pública.  
  
 Si quiere ver una discusión en profundidad sobre la proyección del lenguaje C\+\+\/CX y cómo funciona tras los bastidores, consulte estas publicaciones de blogs:  
  
1.  [C\+\+\/CX Part 0 of \[n\]: An Introduction \(C\+\+\/CX Parte 0 de \[n\]: introducción\)](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
2.  [C\+\+\/CX Part 0 of \[n\]: An Introduction \(C\+\+\/CX Parte 0 de \[n\]: introducción\)](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
3.  [C\+\+\/CX Part 2 of \[n\]: Types That Wear Hats \(C\+\+\/CX Parte 2 de \[n\]: tipos que llevan sombreros\)](http://blogs.msdn.com/b/vcblog/archive/2012/09/17/cxxcxpart02typesthatwearhats.aspx)  
  
4.  [C\+\+\/CX Part 3 of \[n\]: Under Construction \(C\+\+\/CX Parte 3 de \[n\]: en construcción\)](http://blogs.msdn.com/b/vcblog/archive/2012/10/05/cxxcxpart03underconstruction.aspx)  
  
5.  [C\+\+\/CX Part 4 of \[n\]: Static Member Functions \(C\+\+\/CX Parte 4 de \[n\]: funciones miembro estáticas\)](http://blogs.msdn.com/b/vcblog/archive/2012/10/19/cxxcxpart04staticmemberfunctions.aspx)  
  
## Archivos de metadatos de Windows \(.winmd\)  
 Cuando compilas una aplicación de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] escrita en C\+\+, el compilador genera el ejecutable en código máquina nativo y también genera un archivo de metadatos de Windows \(.winmd\) independiente que contiene descripciones de los tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] públicos, que incluyen clases, structs, enumeraciones, interfaces, interfaces parametrizadas y delegados. El formato de los metadatos se parece al formato que se utiliza en los ensamblados de .NET Framework.  En un componente de C\+\+, el archivo .winmd solo contiene metadatos; el código ejecutable reside en un archivo independiente. Este es el caso de los componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] incluidos con Windows. El nombre de archivo WinMD tiene que coincidir o ser un prefijo del espacio de nombres raíz en el código fuente. \(Para los lenguajes de .NET Framework, el archivo de .winmd contiene el código y los metadatos, como un ensamblado de .NET Framework\).  
  
 Los metadatos del archivo de .winmd representan la superficie publicada de tu código. Los tipos publicados son visibles para otras aplicaciones de [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] con independencia del lenguaje en que se escriban esas otras aplicaciones. Por consiguiente, los metadatos, o tu código publicado, solo pueden contener tipos especificados por el sistema de tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. Las construcciones de lenguaje específicas de C\+\+, como clases, matrices, plantillas o contenedores STL normales, no se pueden publicar en los metadatos porque una aplicación cliente de JavaScript o de C\# no sabría lo que debería hacer con ellas.  
  
 Que un tipo o un método estén visibles en los metadatos depende de los modificadores de accesibilidad que se les aplique. Para que esté visible, un tipo se debe declarar en un espacio de nombres y como público. Una clase ref pública se permite como tipo auxiliar interno en tu código; simplemente no está visible en los metadatos. Incluso en una clase ref pública, no todos los miembros están visibles necesariamente. En la tabla siguiente se muestra la relación entre los especificadores de acceso de C\+\+ en una clase ref pública, y la visibilidad de los metadatos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]:  
  
|||  
|-|-|  
|**Publicado en metadatos**|**No publicado en metadatos**|  
|public|private|  
|protected|internal|  
|público protegido|privado protegido|  
  
 Puedes utilizar el **Explorador de objetos** para ver el contenido de los archivos .winmd. Los componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] incluidos con Windows están en el archivo Windows.winmd. El archivo default.winmd contiene los tipos fundamentales que se utilizan en [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] y el archivo platform.winmd contiene tipos adicionales del espacio de nombres Platform. De forma predeterminada, estos tres archivos .winmd se incluyen en todos los proyectos de C\+\+ para aplicaciones de la [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)].  
  
> [!TIP]
>  Los tipos de [Platform::Collections \(Espacio de nombres\)](../cppcx/platform-collections-namespace.md) no aparecen en el archivo .winmd porque no son públicos. Son implementaciones específicas de C\+\+ privadas de las interfaces que se definen en `Windows::Foundation::Collections`. Una aplicación de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] escrita en JavaScript o C\# no sabe qué es un objeto [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md), pero puede utilizar un objeto `Windows::Foundation::Collections::IVector`. Los tipos de `Platform::Collections` se definen en collection.h.  
  
## Sistema de tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] en [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]  
 En las secciones siguientes se describen las características principales del sistema de tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] y cómo se admiten en [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)].  
  
### Espacios de nombres  
 Todos los tipos de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] deben declararse dentro de un espacio de nombres; la propia API de Windows se organiza mediante espacios de nombres. Un archivo .winmd debe tener el mismo nombre que el espacio de nombres de la raíz. Por ejemplo, se pueden crear instancias de una clase denominada A.B.C.MyClass solo si está definida en un archivo de metadatos denominado A.winmd, A.B.winmd o A.B.C.winmd. El nombre de la DLL no tiene que coincidir con el nombre del archivo .winmd.  
  
 La propia API de Windows se ha reinventado como una biblioteca de clases correctamente factorizada que se organiza mediante espacios de nombres.  Todos los componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] se declaran en los espacios de nombres Windows.\*.  
  
 Para obtener más información, consulta [Visibilidad de espacios de nombres y tipos](../cppcx/namespaces-and-type-visibility-c-cx.md).  
  
### Tipos fundamentales  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] define los tipos fundamentales siguientes: UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, Double, Char16, Boolean y String.[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] admite los tipos numéricos fundamentales en su espacio de nombres predeterminado como uint16, uint32, uint64, int16, int32, int64, float32, float64 y char16. Boolean y String también se definen en el espacio de nombres Platform.  
  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] también define uint8, equivalente a `unsigned char`, que no se admite en [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] y no se puede utilizar en las API públicas.  
  
 Un tipo fundamental puede convertirse en un tipo que acepte valores NULL incluyéndolo en una [interfaz Platform::IBox](../cppcx/platform-ibox-interface.md). Para obtener más información, consulta [Value \(Clases y structs\)](../cppcx/value-classes-and-structs-c-cx.md).  
  
 Para obtener más información sobre los tipos fundamentales, consulta [Tipos fundamentales](../cppcx/fundamental-types-c-cx.md).  
  
### Cadenas  
 Una cadena de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] es una secuencia inmutable de caracteres UNICODE de 16 bits. Una cadena de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] se proyecta como `Platform::String^`. Esta clase proporciona métodos para la construcción, manipulación y conversión de cadenas a un tipo `wchar_t` y desde dicho tipo.  
  
 Para obtener más información, consulta [Cadenas](../cppcx/strings-c-cx.md).  
  
### Matrices  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] admite matrices unidimensionales de cualquier tipo. No se admiten matrices de matrices.  En [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)], las matrices de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] se proyectan como [Platform::Array \(Clase\)](../cppcx/platform-array-class.md).  
  
 Para obtener más información, consulta [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
### Clases ref y structs ref  
 Una clase de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] se proyecta en [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] como una clase ref o un struct ref, porque se copian por referencia. La administración de memoria para clases ref y structs ref se controlan de forma transparente mediante el recuento de referencias. Cuando la última referencia a un objeto sale del ámbito, el objeto se destruye. Una clase ref y un struct ref pueden:  
  
-   Contener como miembros constructores, métodos, propiedades y eventos. Estos miembros pueden tener accesibilidad pública, privada, protegida o interna.  
  
-   Contener definiciones de clases, structs o enumeraciones de tipo anidado privado.  
  
-   Heredar directamente de una clase base e implementar cualquier número de interfaces. Todas las clases ref se pueden convertir implícitamente a [Platform::Object \(Clase\)](../cppcx/platform-object-class.md) y pueden invalidar sus métodos virtuales como [Object::ToString](../cppcx/object-tostring-method-c-cx.md).  
  
 Una clase ref que tenga un constructor público se debe declarar como sellada, para evitar la derivación adicional.  
  
 Para obtener más información, consulta [Clases ref y structs ref](../cppcx/ref-classes-and-structs-c-cx.md).  
  
### Clases y structs de valor  
 Una clase de valor o un struct de valor representan una estructura de datos básicos y solo contienen campos, que pueden ser clases de valor, structs de valor o `Platform::String^` de tipo.  Los structs de valor y las clases de valor se copian por valor.  
  
 Un struct de valor se puede convertir en un struct que acepte valores NULL incluyéndolo en una interfaz IBox.  
  
 Para obtener más información, consulta [Value \(Clases y structs\)](../cppcx/value-classes-and-structs-c-cx.md).  
  
### Clases parciales  
 La característica de clases parciales permite definir una clase en varios archivos. Se utiliza principalmente para permitir a las herramientas de generación de código como el editor de XAML modificar un archivo sin tocar el archivo que estás editando.  
  
 Para obtener más información, consulta [Clases parciales](../cppcx/partial-classes-c-cx.md).  
  
### Propiedades  
 Una propiedad es un miembro de datos públicos de cualquier tipo de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] y se implementa como un par de métodos get y set. El código de cliente tiene acceso a una propiedad como si fuera un campo público. Una propiedad que no requiere código de tipo get o set personalizado se conoce como *propiedad trivial* y se puede declarar sin métodos de tipo get o set explícitos.  
  
 Para obtener más información, consulta [Propiedades](../cppcx/properties-c-cx.md).  
  
### Colecciones de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] en [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] define un conjunto de interfaces para los tipos de colección que cada lenguaje implementa de manera propia.[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] proporciona implementaciones en [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md), [Platform::Collections::Map \(Clase\)](../cppcx/platform-collections-map-class.md) y otros tipos de colección concretos relacionados, que son compatibles con sus homólogos de la Biblioteca de plantillas estándar \(STL\).  
  
 Para obtener más información, consulta [Colecciones](../cppcx/collections-c-cx.md).  
  
### Clases ref de plantilla  
 Las clases privadas y las clases ref internas se pueden convertir en plantillas y personalizarse para usos concretos.  
  
 Para obtener más información, consulta [Clases ref de plantilla](../cppcx/template-ref-classes-c-cx.md).  
  
### Interfaces  
 Una interfaz de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] define un conjunto de propiedades, métodos y eventos públicos que una clase ref o un struct ref deben implementar si heredan de la interfaz.  
  
 Para obtener más información, consulta [Interfaces](../cppcx/interfaces-c-cx.md).  
  
### Enumeraciones  
 Una clase de enumeración en [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] es similar a una enumeración con ámbito en C\+\+. El tipo subyacente es int32, a menos que se aplique el atributo \[Flags\]; en ese caso, el tipo subyacente es uint32.  
  
 Para obtener más información, consulta [Enumeraciones](../cppcx/enums-c-cx.md).  
  
### Delegados  
 Un delegado en [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] es análogo a un objeto std::function en C\+\+. Es un tipo especial de clase ref que se utiliza para invocar funciones proporcionadas por el cliente que tienen firmas compatibles.  Los delegados se utilizan con mucha frecuencia en [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] como el tipo de un evento.  
  
 Para obtener más información, consulta [Delegados](../cppcx/delegates-c-cx.md).  
  
### Excepciones  
 En C\+\+\/CX, puedes detectar tipos de excepción personalizados, tipos [std::exception](../Topic/exception%20Class1.md) y tipos [Platform::Exception](../cppcx/platform-exception-class.md).  
  
 Para obtener más información, consulta [Excepciones](../cppcx/exceptions-c-cx.md).  
  
### Eventos  
 Un evento es un miembro público en una clase ref o un struct ref cuyo tipo es un tipo delegado. Un evento solo puede ser invocado, es decir desencadenado, por la clase propietaria. Sin embargo, el código de cliente puede proporcionar sus propias funciones, que se denominan controladores de eventos y se invocan cuando la clase propietaria desencadena el evento.  
  
 Para obtener más información, consulta [Eventos](../cppcx/events-c-cx.md).  
  
### Conversión  
 C\+\+\/CX admite los operadores de conversión estándar de C\+\+ [static\_cast](../cpp/static-cast-operator.md), [dynamic\_cast](../cpp/dynamic-cast-operator.md) y [reinterpret\_cast](../cpp/reinterpret-cast-operator.md), y también el operador [safe\_cast](../Topic/safe_cast%20\(C++%20Component%20Extensions\).md) que es específico de C\+\+\/CX.  
  
 Para obtener más información, consulta [Convertir](../cppcx/casting-c-cx.md).  
  
### Boxing  
 Una variable a la que se le ha aplicado una conversión boxing es un tipo de valor incluido en un tipo de referencia usado en situaciones donde se es necesaria una semántica de referencia.  
  
 Para obtener más información, consulta [Conversión boxing](../cppcx/boxing-c-cx.md).  
  
### Atributos  
 Un atributo es un valor de metadatos que se puede aplicar a cualquier tipo o miembro de tipo de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] y se puede inspeccionar en tiempo de ejecución.[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] define un conjunto de atributos comunes en el espacio de nombres `Windows::Foundation::Metadata`. Los atributos definidos por el usuario en interfaces públicas no se admiten en esta versión e [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
## Marcar la API como en desuso  
 Describe cómo marcar las API públicas como desusadas utilizando el mismo atributo que el usado por los tipos del sistema de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
 Para obtener más información, consulta [Dejar en desuso tipos y miembros](../cppcx/deprecating-types-and-members-c-cx.md).  
  
## Vea también  
 [Referencia del lenguaje Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)