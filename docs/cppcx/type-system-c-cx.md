---
title: Sistema de tipos (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6137203176722316b802a1da5bb2e67dba36848a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594026"
---
# <a name="type-system-ccx"></a>Sistema de tipos (C++/CX)
Mediante el uso de la arquitectura en tiempo de ejecución de Windows, puede usar C++ / c++ / CX, Visual Basic, Visual C# y JavaScript para escribir aplicaciones y componentes que directamente acceso a la API de Windows e interoperan con otras aplicaciones de Windows Runtime y los componentes. Plataforma de Windows universales que se escriben en C++ se compilan en código nativo que se ejecuta directamente en la CPU. Plataforma de Windows universales que se escriben en C# o Visual Basic se compilan en lenguaje intermedio de Microsoft (MSIL) y ejecutan en common language runtime (CLR). Plataforma de Windows universales que se escriben en JavaScript se ejecutan en un entorno de tiempo de ejecución. Los propios componentes del sistema operativo Windows en tiempo de ejecución se escriben en C++ y se ejecutan como código nativo. Todos estos componentes y aplicaciones de la plataforma Universal de Windows se comunican directamente a través de la interfaz binaria de aplicación de Windows en tiempo de ejecución (ABI).  
  
 Para habilitar la compatibilidad con el tiempo de ejecución de Windows en una locución de C++ moderno, Microsoft creó C++ / c++ / CX. C++ / c++ / CX proporciona implementaciones de los tipos fundamentales de Windows en tiempo de ejecución que permiten a las aplicaciones de C++ y componentes para comunicarse a través de ABI con aplicaciones escritas en otros lenguajes y tipos base integrados. Puede trabajar con cualquier tipo en tiempo de ejecución de Windows, o crear clases, structs, interfaces y otros tipos definidos por el usuario que pueden usarse en otras aplicaciones de la plataforma Universal de Windows y componentes. una aplicación de plataforma Universal de Windows escrita en C++ / c++ / CX también puede usar clases C++ normales y las estructuras, siempre no tengan accesibilidad pública.  
  
 Si quiere ver una discusión en profundidad sobre la proyección del lenguaje C++/CX y cómo funciona tras los bastidores, consulte estas publicaciones de blogs:  
  
1.  [C++ / c++ / CX parte 0 de \[n\]: Introducción](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)  
  
2.  [C++ / c++ / CX parte 1 de \[n\]: una clase Simple](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)  
  
3.  [C++ / c++ / CX parte 2 de \[n\]: tipos que usan sombreros](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)  
  
4.  [C++ / c++ / CX parte 3 de \[n\]: en construcción](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)  
  
5.  [C++ / c++ / CX parte 4 de \[n\]: las funciones miembro estáticas](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)  
  
## <a name="windows-metadata-winmd-files"></a>Archivos de metadatos de Windows (.winmd)  
 Al compilar una aplicación de plataforma Universal de Windows que está escrita en C++, el compilador genera el archivo ejecutable en código máquina nativo y también genera un archivo de metadatos (.winmd) independiente de Windows que contiene las descripciones de los tipos públicos de Windows en tiempo de ejecución, que incluyen clases, estructuras, enumeraciones, interfaces, interfaces parametrizadas y delegados. El formato de los metadatos se parece al formato que se utiliza en los ensamblados de .NET Framework.  En un componente de C++, el archivo .winmd solo contiene metadatos; el código ejecutable reside en un archivo independiente. Este es el caso de los componentes de Windows en tiempo de ejecución que se incluyen con Windows. El nombre de archivo WinMD tiene que coincidir o ser un prefijo del espacio de nombres raíz en el código fuente. (Para los lenguajes de .NET Framework, el archivo de .winmd contiene el código y los metadatos, como un ensamblado de .NET Framework).  
  
 Los metadatos del archivo de .winmd representan la superficie publicada de tu código. Los tipos publicados son visibles para otras plataformas de Windows universales independientemente del lenguaje se escriban esas otras aplicaciones. Por lo tanto, los metadatos, o tu código publicado, solo puede contener tipos especificados por el sistema de tipos en tiempo de ejecución de Windows. Las construcciones de lenguaje específicas de C++, como clases, matrices, plantillas o contenedores STL normales, no se pueden publicar en los metadatos porque una aplicación cliente de JavaScript o de C# no sabría lo que debería hacer con ellas.  
  
 Que un tipo o un método estén visibles en los metadatos depende de los modificadores de accesibilidad que se les aplique. Para que esté visible, un tipo se debe declarar en un espacio de nombres y como público. Una clase ref pública se permite como tipo auxiliar interno en tu código; simplemente no está visible en los metadatos. Incluso en una clase ref pública, no todos los miembros están visibles necesariamente. La tabla siguiente muestra la relación entre los especificadores de acceso de C++ en una clase ref pública y la visibilidad de los metadatos de Windows en tiempo de ejecución:  
  
|||  
|-|-|  
|**Publicado en metadatos**|**No publicado en metadatos**|  
|public|private|  
|protected|internal|  
|público protegido|privado protegido|  
  
 Puedes utilizar el **Explorador de objetos** para ver el contenido de los archivos .winmd. Los componentes de Windows en tiempo de ejecución que se incluyen con Windows están en el archivo Windows.winmd. El archivo default.winmd contiene los tipos fundamentales que se usan en C / c++ / CX y platform.winmd contiene tipos adicionales del espacio de nombres de plataforma. De forma predeterminada, estos tres archivos .winmd se incluyen en cada proyecto de C++ para aplicaciones de la plataforma Universal de Windows.  
  
> [!TIP]
>  Los tipos de [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) no aparecen en el archivo .winmd porque no son públicos. Son implementaciones específicas de C++ privadas de las interfaces que se definen en `Windows::Foundation::Collections`. Una aplicación de Windows en tiempo de ejecución que está escrita en JavaScript o C# no sabe qué es un [Platform::Collections::Vector clase](../cppcx/platform-collections-vector-class.md) es, pero puede utilizar un `Windows::Foundation::Collections::IVector`. Los tipos de `Platform::Collections` se definen en collection.h.  
  
## <a name="windows-runtime-type-system-in-ccx"></a>Sistema de tipos en tiempo de ejecución de Windows en C++ / c++ / CX  
 Las secciones siguientes describen las características principales del sistema de tipos en tiempo de ejecución de Windows y cómo se admiten en C / c++ / CX.  
  
### <a name="namespaces"></a>Espacios de nombres  
 Todos los tipos en tiempo de ejecución de Windows deben declararse dentro de un espacio de nombres; la propia API de Windows se organiza mediante espacios de nombres. Un archivo .winmd debe tener el mismo nombre que el espacio de nombres de la raíz. Por ejemplo, se pueden crear instancias de una clase denominada A.B.C.MyClass solo si está definida en un archivo de metadatos denominado A.winmd, A.B.winmd o A.B.C.winmd. El nombre de la DLL no tiene que coincidir con el nombre del archivo .winmd.  
  
 La propia API de Windows se ha reinventado como una biblioteca de clases correctamente factorizada que se organiza mediante espacios de nombres.  Todos los componentes de Windows en tiempo de ejecución se declaran en los espacios de nombres Windows.*.  
  
 Para obtener más información, consulte [espacios de nombres y la visibilidad de tipos](../cppcx/namespaces-and-type-visibility-c-cx.md).  
  
### <a name="fundamental-types"></a>Tipos fundamentales  
 El tiempo de ejecución de Windows se define la tipos fundamentales siguientes:, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, Double, Char16, Boolean y cadena. C++ / c++ / CX admite los tipos numéricos fundamentales en su espacio de nombres predeterminado como uint16, uint32, uint64, int16, int32, int64, float32, float64 y char16. Boolean y String también se definen en el espacio de nombres Platform.  
  
 C++ / c++ / CX también define uint8, equivalente a `unsigned char`, que no se admite en el tiempo de ejecución de Windows y no se puede usar en las API públicas.  
  
 Un tipo fundamental puede convertirse en un tipo que acepte valores NULL incluyéndolo en una [interfaz Platform::IBox](../cppcx/platform-ibox-interface.md) . Para obtener más información, consulta [Clases y structs de valor](../cppcx/value-classes-and-structs-c-cx.md).  
  
 Para obtener más información sobre los tipos fundamentales, consulta [Tipos fundamentales](../cppcx/fundamental-types-c-cx.md)  
  
### <a name="strings"></a>Cadenas  
 Una cadena en tiempo de ejecución de Windows es una secuencia inmutable de caracteres UNICODE de 16 bits. Una cadena en tiempo de ejecución de Windows se proyecta como `Platform::String^`. Esta clase proporciona métodos para la construcción, manipulación y conversión de cadenas a un tipo `wchar_t`y desde dicho tipo.  
  
 Para obtener más información, consulta [Cadenas](../cppcx/strings-c-cx.md).  
  
### <a name="arrays"></a>Matrices  
 El tiempo de ejecución de Windows admite 1-dimensional matrices de cualquier tipo. No se admiten matrices de matrices.  En C / c++ / CX, matrices de Windows en tiempo de ejecución se proyectan como el [clase Platform:: Array](../cppcx/platform-array-class.md).  
  
 Para obtener más información, consulte [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)  
  
### <a name="ref-classes-and-structs"></a>Clases ref y structs ref  
 Se prevé que una clase en tiempo de ejecución de Windows en C++ / c++ / CX como una clase ref o un struct ref, porque se copian por referencia. La administración de memoria para clases ref y structs ref se controlan de forma transparente mediante el recuento de referencias. Cuando la última referencia a un objeto sale del ámbito, el objeto se destruye. Una clase ref y un struct ref pueden:  
  
-   Contener como miembros constructores, métodos, propiedades y eventos. Estos miembros pueden tener accesibilidad pública, privada, protegida o interna.  
  
-   Contener definiciones de clases, structs o enumeraciones de tipo anidado privado.  
  
-   Heredar directamente de una clase base e implementar cualquier número de interfaces. Todas las clases ref se pueden convertir implícitamente a [Platform::Object Class](../cppcx/platform-object-class.md) y pueden invalidar sus métodos virtuales como [Object::ToString](../cppcx/platform-object-class.md#tostring).  
  
 Una clase ref que tenga un constructor público se debe declarar como sellada, para evitar la derivación adicional.  
  
 Para obtener más información, consulta [Clases ref y structs ref](../cppcx/ref-classes-and-structs-c-cx.md)  
  
### <a name="value-classes-and-structs"></a>Clases y structs de valor  
 Una clase de valor o un struct de valor representan una estructura de datos básicos y solo contienen campos, que pueden ser clases de valor, structs de valor o `Platform::String^`de tipo.  Los structs de valor y las clases de valor se copian por valor.  
  
 Un struct de valor se puede convertir en un struct que acepte valores NULL incluyéndolo en una interfaz IBox.  
  
 Para obtener más información, consulta [Clases y structs de valor](../cppcx/value-classes-and-structs-c-cx.md).  
  
### <a name="partial-classes"></a>Clases parciales  
 La característica de clases parciales permite definir una clase en varios archivos. Se utiliza principalmente para permitir a las herramientas de generación de código como el editor de XAML modificar un archivo sin tocar el archivo que estás editando.  
  
 Para obtener más información, consulta [Clases parciales](../cppcx/partial-classes-c-cx.md)  
  
### <a name="properties"></a>Propiedades  
 Una propiedad es un miembro de datos públicos de cualquier tipo en tiempo de ejecución de Windows y se implementa como un par de métodos get/set. El código de cliente tiene acceso a una propiedad como si fuera un campo público. Una propiedad que no requiere código de tipo get o set personalizado se conoce como *propiedad trivial* y se puede declarar sin métodos de tipo get o set explícitos.  
  
 Para obtener más información, consulta [Propiedades](../cppcx/properties-c-cx.md).  
  
### <a name="windows-runtime-collections-in-ccx"></a>Colecciones de Windows Runtime en C++ / c++ / CX  
 El tiempo de ejecución de Windows se define un conjunto de interfaces para los tipos de colección que cada lenguaje implementa de manera propia. C++ / c++ / CX proporciona implementaciones en el [Platform::Collections::Vector clase](../cppcx/platform-collections-vector-class.md), [Platform::Collections::Map clase](../cppcx/platform-collections-map-class.md)y otros tipos de colección concretos relacionados, que son compatibles con sus Equivalentes de biblioteca de plantillas (STL) estándar.  
  
 Para obtener más información, consulte [colecciones](../cppcx/collections-c-cx.md).  
  
### <a name="template-ref-classes"></a>Clases ref de plantilla  
 Las clases privadas y las clases ref internas se pueden convertir en plantillas y personalizarse para usos concretos.  
  
 Para obtener más información, consulta [Clases ref de plantilla](../cppcx/template-ref-classes-c-cx.md).  
  
### <a name="interfaces"></a>Interfaces  
 Una interfaz de Windows Runtime define un conjunto de propiedades públicas, métodos y eventos que una clase ref o un struct ref debe implementar si se hereda de la interfaz.  
  
 Para más información, vea [Interfaces](../cppcx/interfaces-c-cx.md).  
  
### <a name="enums"></a>Enumeraciones  
 Una clase de enumeración en tiempo de ejecución de Windows es similar a una enumeración con ámbito en C++. El tipo subyacente es int32, a menos que se aplique el atributo [Flags]; en ese caso, el tipo subyacente es uint32.  
  
 Para obtener más información, consulta [Enumeraciones](../cppcx/enums-c-cx.md).  
  
### <a name="delegates"></a>Delegados  
 Un delegado en el tiempo de ejecución de Windows es análogo a un objeto std:: Function en C++. Es un tipo especial de clase ref que se utiliza para invocar funciones proporcionadas por el cliente que tienen firmas compatibles.  Los delegados se usan normalmente en el tiempo de ejecución de Windows como el tipo de un evento.  
  
 Para obtener más información, vea [Delegados (Guía de programación de C#)](../cppcx/delegates-c-cx.md).  
  
### <a name="exceptions"></a>Excepciones  
 En C++/CX, puedes detectar tipos de excepción personalizados, tipos [std::exception](../standard-library/exception-class.md) y tipos [Platform::Exception](../cppcx/platform-exception-class.md) .  
  
 Para obtener más información, consulta [Excepciones](../cppcx/exceptions-c-cx.md).  
  
### <a name="events"></a>Eventos  
 Un evento es un miembro público en una clase ref o un struct ref cuyo tipo es un tipo delegado. Un evento solo puede ser invocado, es decir desencadenado, por la clase propietaria. Sin embargo, el código de cliente puede proporcionar sus propias funciones, que se denominan controladores de eventos y se invocan cuando la clase propietaria desencadena el evento.  
  
 Para obtener más información, consulta [Eventos](../cppcx/events-c-cx.md).  
  
### <a name="casting"></a>Conversión  
 C++/CX admite los operadores de conversión estándar de C++ [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md)y [reinterpret_cast](../cpp/reinterpret-cast-operator.md), y también el operador **safe_cast** que es específico de C++/CX.  
  
 Para obtener más información, consulta [Conversión](../cppcx/casting-c-cx.md).  
  
### <a name="boxing"></a>Boxing  
 Una variable a la que se le ha aplicado una conversión boxing es un tipo de valor incluido en un tipo de referencia usado en situaciones donde se es necesaria una semántica de referencia.  
  
 Para obtener más información, consulta [Boxing](../cppcx/boxing-c-cx.md).  
  
### <a name="attributes"></a>Atributos  
 Un atributo es un valor de metadatos que se puede aplicar a cualquier tipo de tiempo de ejecución de Windows o un miembro de tipo y se puede inspeccionar en tiempo de ejecución. El tiempo de ejecución de Windows se define un conjunto de atributos comunes en el `Windows::Foundation::Metadata` espacio de nombres. Atributos definidos por el usuario en las interfaces públicas no se admiten en tiempo de ejecución de Windows en esta versión.  
  
## <a name="api-deprecation"></a>Marcar la API como en desuso  
 Describe cómo marcar las API públicas como desusadas utilizando el mismo atributo utilizado por los tipos de sistema de Windows en tiempo de ejecución.  
  
 Para obtener más información, consulte [dejar en desuso tipos y miembros](../cppcx/deprecating-types-and-members-c-cx.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
